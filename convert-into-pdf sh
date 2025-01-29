#!/bin/bash

# Check if a file is provided
if [ -z "$1" ]; then
  echo "Usage: $0 <path-to-docx-file>"
  exit 1
fi

# Check if LibreOffice is installed
if ! command -v libreoffice &> /dev/null
then
    echo "LibreOffice could not be found, please install it first."
    exit 1
fi

# Convert the docx to pdf using LibreOffice
libreoffice --headless --convert-to pdf "$1"

if [ $? -eq 0 ]; then
  echo "Conversion successful: $(basename "$1" .docx).pdf"
  
  # Call Python script to send the email
  python3 send_email.py "$(basename "$1" .docx).pdf"
else
  echo "Conversion failed."
fi

