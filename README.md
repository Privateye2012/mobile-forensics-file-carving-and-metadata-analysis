## Mobile Forensics – File Carving and Metadata Analysis

### Overview
This repository documents a hands-on digital forensics laboratory focused on
low-level forensic techniques applied to mobile device data, including file
carving, hexadecimal analysis, and metadata extraction.

The activity was developed as part of the Digital Forensics and Cyber Threat
Intelligence microcredential (Week 3).

The original report was written in Portuguese, as the course was taught in Portuguese.
This repository exists to demonstrate practical forensic methodology, low-level
analysis skills, and evidentiary validation in a controlled academic environment.

---

### Objectives
- Perform low-level forensic analysis using hexadecimal inspection
- Recover deleted or hidden files using file carving techniques
- Identify file boundaries using magic numbers
- Extract and validate ZIP and JPEG files from raw disk images
- Calculate cryptographic hashes to ensure data integrity
- Extract and analyze metadata from digital images
- Identify GPS location data from EXIF metadata

---

### Lab Environment
- Forensic Images: RAW / DD format disk images
- Analysis Tools:
  - HxD Hex Editor
  - HashCalc
  - ExifTool
  - 7-Zip
  - Windows command-line tools

All analysis was performed on forensic copies to preserve evidence integrity.

---

## File Carving Methodology

File carving is a forensic technique used to recover files directly from raw
data by identifying file signatures (magic numbers), without relying on a file
system structure.

This technique is essential when file systems are corrupted, deleted, or absent.

---

### ZIP File Recovery (challenge.dd)

- Identified ZIP file header using magic number: 50 4B 03 04
- Identified ZIP End of Central Directory signature: 50 4B 05 06
- Calculated file boundaries based on EOCD structure
- Extracted the file by selecting the corresponding byte range
- Saved the recovered file as carved.zip
- Verified successful extraction using 7-Zip
- Calculated MD5 hash to ensure integrity

Recovered ZIP file hash:
- MD5: ed2a74f3a68710ee41c4004a8f5e2071

---

### JPEG File Recovery and Metadata Analysis (challenge.dd)

- Identified JPEG start marker: FF D8 FF E0
- Identified JPEG end marker: FF D9
- Extracted image by selecting byte range
- Saved recovered file as image1.jpg
- Verified successful visualization
- Calculated MD5 hash for integrity validation

Recovered JPEG hash:
- MD5: 0190eed3587d5682653c74230cee8f38

---

### EXIF Metadata Extraction

- Used ExifTool to extract all time and location metadata
- Identified GPS latitude, longitude, and altitude
- Converted GPS coordinates to decimal format
- Mapped coordinates using online mapping services

Key findings:
- GPSLatitude: 40.689253 N
- GPSLongitude: 74.044548 W
- Location identified: Statue of Liberty, New York

---

### JPEG Recovery from challenge2.dd

- Identified multiple JPEG files using FF D8 and FF D9 markers
- Extracted three separate JPEG files
- Calculated MD5 hashes for each recovered image
- Verified visualization results

Recovered files:
- image21.jpg (did not open)
  - MD5: 6f91f6e6197d8e5595f16af91795f1d6

- image22.jpg (opened successfully)
  - MD5: 0431b49af2c76597410e481baba20e31

- image23.jpg (opened successfully)
  - MD5: e8be7c8a39f6e1a298c9318887fd7f1e

---

### Thumbnail Extraction Attempt

- Attempted EXIF thumbnail extraction using ExifTool
- Analyzed EXIF structures for embedded previews
- Documented unsuccessful extraction attempts
- Demonstrated forensic reasoning and validation

---

Results Summary
- Successful recovery of ZIP and JPEG files via file carving
- Integrity confirmed using cryptographic hashes
- GPS metadata successfully extracted and geolocated
- Demonstrated effectiveness of low-level forensic techniques

---

### Ethical and Legal Considerations
- All activities were conducted in a controlled academic environment
- No real mobile devices or personal data were involved
- Procedures respected forensic ethics and evidence integrity principles
- The work focused exclusively on educational objectives

---

