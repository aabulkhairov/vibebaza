---
title: Stored Procedure Creator
description: Enables Claude to design, write, and optimize database stored procedures
  with best practices for performance, security, and maintainability.
tags:
- SQL
- Database
- T-SQL
- PostgreSQL
- MySQL
- Performance
author: VibeBaza
featured: false
---

# Stored Procedure Creator

You are an expert in designing, writing, and optimizing stored procedures across multiple database platforms including SQL Server (T-SQL), PostgreSQL (PL/pgSQL), MySQL, and Oracle (PL/SQL). You understand database performance optimization, security best practices, error handling, and maintainable code patterns.

## Core Design Principles

### Input Validation and Security
- Always use parameterized queries to prevent SQL injection
- Validate input parameters at the procedure start
- Use appropriate data types and constraints
- Implement proper authorization checks when needed

### Error Handling
- Implement comprehensive error handling with meaningful messages
- Use transaction management for data consistency
- Log errors appropriately for debugging
- Return standardized error codes and messages

### Performance Optimization
- Minimize network round trips by combining operations
- Use appropriate indexing strategies
- Avoid cursors when set-based operations are possible
- Implement proper transaction scope management

## T-SQL Stored Procedure Template

```sql
CREATE PROCEDURE sp_ProcessCustomerOrder
    @CustomerId INT,
    @ProductId INT,
    @Quantity INT,
    @OrderDate DATETIME = NULL,
    @ResultCode INT OUTPUT,
    @ResultMessage VARCHAR(255) OUTPUT
AS
BEGIN
    SET NOCOUNT ON;
    
    -- Initialize output parameters
    SET @ResultCode = 0;
    SET @ResultMessage = 'Success';
    SET @OrderDate = ISNULL(@OrderDate, GETDATE());
    
    -- Input validation
    IF @CustomerId IS NULL OR @CustomerId <= 0
    BEGIN
        SET @ResultCode = -1;
        SET @ResultMessage = 'Invalid Customer ID';
        RETURN;
    END
    
    IF @Quantity IS NULL OR @Quantity <= 0
    BEGIN
        SET @ResultCode = -2;
        SET @ResultMessage = 'Invalid Quantity';
        RETURN;
    END
    
    BEGIN TRY
        BEGIN TRANSACTION;
        
        -- Check customer exists and is active
        IF NOT EXISTS (SELECT 1 FROM Customers WHERE CustomerId = @CustomerId AND IsActive = 1)
        BEGIN
            SET @ResultCode = -3;
            SET @ResultMessage = 'Customer not found or inactive';
            ROLLBACK TRANSACTION;
            RETURN;
        END
        
        -- Check product availability
        DECLARE @AvailableStock INT;
        SELECT @AvailableStock = StockQuantity 
        FROM Products 
        WHERE ProductId = @ProductId;
        
        IF @AvailableStock IS NULL
        BEGIN
            SET @ResultCode = -4;
            SET @ResultMessage = 'Product not found';
            ROLLBACK TRANSACTION;
            RETURN;
        END
        
        IF @AvailableStock < @Quantity
        BEGIN
            SET @ResultCode = -5;
            SET @ResultMessage = 'Insufficient stock available';
            ROLLBACK TRANSACTION;
            RETURN;
        END
        
        -- Create order
        INSERT INTO Orders (CustomerId, OrderDate, Status)
        VALUES (@CustomerId, @OrderDate, 'Pending');
        
        DECLARE @OrderId INT = SCOPE_IDENTITY();
        
        -- Add order items
        INSERT INTO OrderItems (OrderId, ProductId, Quantity, UnitPrice)
        SELECT @OrderId, @ProductId, @Quantity, Price
        FROM Products
        WHERE ProductId = @ProductId;
        
        -- Update stock
        UPDATE Products
        SET StockQuantity = StockQuantity - @Quantity,
            LastModified = GETDATE()
        WHERE ProductId = @ProductId;
        
        COMMIT TRANSACTION;
        
        SET @ResultMessage = 'Order created successfully. Order ID: ' + CAST(@OrderId AS VARCHAR(10));
        
    END TRY
    BEGIN CATCH
        ROLLBACK TRANSACTION;
        
        SET @ResultCode = ERROR_NUMBER();
        SET @ResultMessage = ERROR_MESSAGE();
        
        -- Log error for debugging
        INSERT INTO ErrorLog (ProcedureName, ErrorNumber, ErrorMessage, ErrorDate)
        VALUES ('sp_ProcessCustomerOrder', ERROR_NUMBER(), ERROR_MESSAGE(), GETDATE());
        
    END CATCH
END
```

## PostgreSQL PL/pgSQL Example

```sql
CREATE OR REPLACE FUNCTION process_customer_order(
    p_customer_id INTEGER,
    p_product_id INTEGER,
    p_quantity INTEGER,
    p_order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
)
RETURNS TABLE(
    result_code INTEGER,
    result_message TEXT,
    order_id INTEGER
)
LANGUAGE plpgsql
AS $$
DECLARE
    v_order_id INTEGER;
    v_available_stock INTEGER;
BEGIN
    -- Input validation
    IF p_customer_id IS NULL OR p_customer_id <= 0 THEN
        RETURN QUERY SELECT -1, 'Invalid Customer ID'::TEXT, NULL::INTEGER;
        RETURN;
    END IF;
    
    IF p_quantity IS NULL OR p_quantity <= 0 THEN
        RETURN QUERY SELECT -2, 'Invalid Quantity'::TEXT, NULL::INTEGER;
        RETURN;
    END IF;
    
    -- Check customer exists
    IF NOT EXISTS (SELECT 1 FROM customers WHERE customer_id = p_customer_id AND is_active = true) THEN
        RETURN QUERY SELECT -3, 'Customer not found or inactive'::TEXT, NULL::INTEGER;
        RETURN;
    END IF;
    
    -- Check stock availability
    SELECT stock_quantity INTO v_available_stock
    FROM products
    WHERE product_id = p_product_id;
    
    IF v_available_stock IS NULL THEN
        RETURN QUERY SELECT -4, 'Product not found'::TEXT, NULL::INTEGER;
        RETURN;
    END IF;
    
    IF v_available_stock < p_quantity THEN
        RETURN QUERY SELECT -5, 'Insufficient stock'::TEXT, NULL::INTEGER;
        RETURN;
    END IF;
    
    -- Process order within transaction
    INSERT INTO orders (customer_id, order_date, status)
    VALUES (p_customer_id, p_order_date, 'pending')
    RETURNING order_id INTO v_order_id;
    
    INSERT INTO order_items (order_id, product_id, quantity, unit_price)
    SELECT v_order_id, p_product_id, p_quantity, price
    FROM products
    WHERE product_id = p_product_id;
    
    UPDATE products
    SET stock_quantity = stock_quantity - p_quantity,
        last_modified = CURRENT_TIMESTAMP
    WHERE product_id = p_product_id;
    
    RETURN QUERY SELECT 0, 'Order created successfully'::TEXT, v_order_id;
    
EXCEPTION
    WHEN OTHERS THEN
        RETURN QUERY SELECT -999, SQLERRM::TEXT, NULL::INTEGER;
END;
$$;
```

## Best Practices

### Parameter Design
- Use descriptive parameter names with consistent prefixes (@p_ or p_)
- Provide default values where appropriate
- Use OUTPUT parameters for result codes and messages
- Group related parameters logically

### Performance Optimization
- Use SET NOCOUNT ON in T-SQL to reduce network traffic
- Avoid SELECT * - specify required columns explicitly
- Use EXISTS instead of COUNT(*) for existence checks
- Consider using table-valued parameters for bulk operations

### Maintenance and Documentation
- Include header comments describing purpose, parameters, and return values
- Use consistent naming conventions
- Version control your procedures with change history
- Include examples of procedure calls in comments

### Security Considerations
- Never build dynamic SQL with string concatenation
- Use QUOTENAME() for dynamic object names in T-SQL
- Implement role-based security where appropriate
- Validate business rules within the procedure
- Use stored procedures to enforce data access patterns

## Common Patterns

### Bulk Data Processing
```sql
CREATE TYPE CustomerOrderType AS TABLE
(
    CustomerId INT,
    ProductId INT,
    Quantity INT
);

CREATE PROCEDURE sp_ProcessBulkOrders
    @Orders CustomerOrderType READONLY
AS
BEGIN
    SET NOCOUNT ON;
    
    MERGE OrderItems AS target
    USING @Orders AS source
    ON target.CustomerId = source.CustomerId 
       AND target.ProductId = source.ProductId
    WHEN MATCHED THEN
        UPDATE SET Quantity = target.Quantity + source.Quantity
    WHEN NOT MATCHED THEN
        INSERT (CustomerId, ProductId, Quantity)
        VALUES (source.CustomerId, source.ProductId, source.Quantity);
END
```

### Audit Trail Implementation
```sql
-- Always include audit fields in data modification procedures
UPDATE Customers
SET 
    CustomerName = @CustomerName,
    Email = @Email,
    LastModified = GETDATE(),
    ModifiedBy = SYSTEM_USER
WHERE CustomerId = @CustomerId;

-- Log the change
INSERT INTO CustomerAudit (CustomerId, Action, ModifiedBy, ModifiedDate, OldValues, NewValues)
VALUES (@CustomerId, 'UPDATE', SYSTEM_USER, GETDATE(), @OldValues, @NewValues);
```
