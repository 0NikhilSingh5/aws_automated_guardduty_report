# <img src = "https://skillicons.dev/icons?i=aws"/> GuardDuty Report Generator

## Overview

This Python script automates the process of generating a comprehensive AWS GuardDuty security findings report. It retrieves security findings from the last 7 days, processes the data, and creates a detailed Excel spreadsheet with key security insights.

## Features

- Fetches GuardDuty findings for the past 7 days
- Supports pagination for handling large numbers of findings
- Generates a timestamped Excel report
- Extracts detailed information about security events
- Applies consistent formatting to the Excel report
- Creates unique filenames to prevent overwriting

## Prerequisites

### Software Requirements
- Python 3.7+
- Required Python Libraries:
  - boto3
  - openpyxl
  - datetime

### AWS Configuration
- AWS Account with GuardDuty enabled
- AWS IAM credentials with permissions to:
  - List GuardDuty detectors
  - Retrieve GuardDuty findings

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Install required dependencies:
   ```bash
   pip install boto3 openpyxl
   ```

3. Configure AWS Credentials:
   - Using AWS CLI: `aws configure`
   - Or set environment variables:
     ```bash
     export AWS_ACCESS_KEY_ID='your-access-key'
     export AWS_SECRET_ACCESS_KEY='your-secret-key'
     export AWS_DEFAULT_REGION='your-region'
     ```

## Usage

Run the script directly:
```bash
python guardduty_report_generator.py
```
## File Requirements

**IMPORTANT**: Requires an existing Excel file named GuardDutyReport.xlsx

This file must be created before running the script
The file should have a structure compatible with the script's column mappings<br>
  Column A: Title<br>
  Column D: EventFirstSeen<br>
  Column E: Severity<br>
  Column G: Description<br>
  Column H: DetectorId<br>
  Column I: AvailabilityZone<br>
  Column J: InstanceId<br>
  Column K: PrivateIpAddress<br>
  Column L: PublicIp<br>
### Notes

* The script will modify the existing GuardDutyReport.xlsx
* A new report will be saved with a unique filename based on the current date
* Ensure the original workbook is not open when running the script

### Output
- An Excel file named `GuardDutyReport-<date>.xlsx`
- Console output showing total findings and report location

## Extracted Information

The report includes the following details for each finding:
- Title
- Event First Seen
- Severity
- Description
- Detector ID
- Availability Zone
- Instance ID
- Private IP Address
- Public IP Address


## Customization

Modify `column_mappings` dictionary to:
- Change column order
- Add or remove fields
- Map different finding attributes

## Error Handling

The script includes basic error handling for:
- Pagination of findings
- Missing or optional attributes
- Unique file naming

## Security Considerations

- Ensure AWS credentials have least-privilege access
- Do not commit credentials to version control
- Use AWS IAM roles and temporary credentials when possible

## Limitations

- Retrieves findings from the last 7 days only
- Limited to 50 findings per API call (configurable)
- Requires active GuardDuty detector

## Troubleshooting

1. Verify AWS credentials
2. Check GuardDuty is enabled in your AWS account
3. Ensure required Python libraries are installed
4. Check network connectivity to AWS services

## Contributing

Contributions are welcome! Please submit pull requests or open issues on the repository.



Made with ❤️ for security monitoring!
