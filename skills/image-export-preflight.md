---
title: "Image export preflight"
description: "Choose an image delivery format, verify one exported file against size, dimensions and transparency requirements, then process the authorized batch."
tags:
  - images
  - export
  - quality-control
author: "Free Photo Editor team"
featured: false
---

# Image export preflight

Use this workflow when someone needs a photo or graphic accepted by an upload form, website, or collaborator. It is an instruction skill from the Free Photo Editor team, with no executable code, API, account, or environment variables. Browser execution needs the agent's existing browser and file-upload/download tools. If those are unavailable, provide the export plan and leave execution unverified.

## Establish the delivery contract

Read the user's destination requirements before processing: accepted formats, maximum bytes, dimensions, and whether transparency must survive. Ask only for a missing requirement that changes the decision. Keep the source file and make a separate delivery copy.

Choose the smallest suitable operation:

| Destination requirement | First operation |
| --- | --- |
| JPEG photograph from a HEIC source | Convert one copy to JPEG; inspect it before converting the batch. |
| PNG graphic with transparency | Preserve PNG; compress or resize the copy if needed. |
| A smaller JPEG or PNG | Compress the copy and compare detail; reduce dimensions only if the destination permits. |
| Editable vector shapes from a flat graphic | Trace to SVG, then inspect paths and visual fidelity. A raster wrapped inside SVG is not a vector trace. |

A format conversion does not require a generative edit. If the original already meets the contract, verify it and return that file; skip unnecessary conversion or recompression. When PNG transparency is required, keep that requirement even if JPEG would be smaller. If the requirements cannot all be met, report the specific conflict.

## Run one sample

For browser processing, open [Free Photo Editor](https://freephotoeditor.io/) and choose the current conversion or compression tool that matches the contract. Inspect the live controls rather than assuming selectors. Upload only the image the user has authorized you to process; avoid bringing unrelated files into a batch.

Run one image through the normal preview and download flow. Use the destination's actual format options and preserve the original. Ordinary conversion, compression, and adjustments run in the browser. Do not invoke an AI tool for this workflow unless the user also requested a content change: AI actions send the required image and instructions to an external processing provider and use shared daily capacity.

After downloading, verify what is actually available:

- Decode or open the downloaded image, checking its real format and dimensions rather than its extension alone.
- Compare its byte size with the limit. If a form says “500 KB” without defining units, target less than 500,000 bytes.
- For transparency, verify the alpha channel or inspect the result over a contrasting background. A white preview alone does not prove alpha was preserved.
- Compare edges, lettering, and orientation with the source. For a vector trace, verify drawing paths and inspect the rendered output.

If a check fails, adjust the export settings and create a new delivery copy. Do not claim a file is accepted by the destination unless it has actually been tested there. Once the sample meets the contract, apply the same decisions to the remaining authorized images and check each output's format and size.

## Return a usable result

Provide the output file and a short record of the observed format, dimensions, bytes, transparency when relevant, and any checks not performed. Say whether the destination itself was tested. Keep proposed settings distinct from completed processing.

## Two examples

**Phone photo for a form:** “Convert this HEIC to JPEG under 500 KB; no dimension limit.” Convert one copy, compress only as needed, then verify it decodes as JPEG and is below 500,000 bytes. Deliver the observed file details; form acceptance remains unverified until tested.

**Transparent mark for a website:** “This PNG must stay transparent and fit under 200 KB.” Keep PNG, compress a copy, and verify alpha and size below 200,000 bytes. If it still exceeds the limit, resize only within the user's allowed dimensions; do not silently switch to JPEG or remove transparency.
