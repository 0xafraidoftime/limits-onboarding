# MBAM Secondary VTD Limit Onboarding

## Overview

This repository contains test evidence and documentation for implementing limit onboarding for MBAM (Municipal Banking and Markets) Secondary VTD (Volcker Trading Desk) within the risk management system.

**JIRA Ticket:** [FICCRISK-32258] - Limit Onboarding for MBAM secondary VTD

## Test Scenario

**Objective:** Verify that breach and no-breach alerts for new limit codes for MBAM Secondary VTD are generated successfully.

### Prerequisites

- Exposures configured in Brisk for MBAM Secondary
- New limit code created in LMS (Limit Management System)
- Access to UAT environment for testing
- Proper measure details and filters provided by Line of Business (LOB)

## Test Setup

### Limit Configuration

The following limit was configured in LMS UAT:

| Field | Value |
|-------|-------|
| Volcker Business Area | MUNICIPAL BANKING AND MARKETS |
| Volcker Trading Desk | MBAM SECONDARY |
| Limit Code | INTRA_FICC_237 |
| Limit Name | INTRA_FICC_MUNI SECONDARY_USD_CS01+1bp |
| Limit Value | 2,000,000.000 |
| Currency | USD |
| Status | Active |
| Risk Factor | Credit Spread |
| Significant Rating | -1 |
| Measure | CS01 |
| Measure Unit | b.p. |
| Entity ID | 8009245 |
| Entity Name | MUNICIPAL BANKING AND MARKETS |

## Test Execution

### 1. VTD CFTC Breach Calculation Job

- Execute the respective VTD CFTC breach calculation job in UAT environment
- Monitor job execution for successful completion

### 2. Breach Testing

To validate breach functionality:
- Artificially trigger exposure values that exceed the configured limit
- Verify breach alert generation and notification system

## Validation Criteria

The test is considered successful when all of the following conditions are met:

### Core Functionality
1. **Breach and No-Breach Emails:** Generated successfully with proper recipient distribution
2. **Data Consistency:** Brisk report exposures match email notification data
3. **Workflow Integration:** End-to-end workflow executes without errors

### Reporting Systems
4. **End of Day Reports:** Generated successfully with accurate limit data
5. **Control Reports:** Proper validation and control mechanisms functioning
6. **Monthly Reports:** Bob job execution completes successfully

## System Components Verified

### Brisk RRA (Production)
- Report generation and data accuracy
- Exposure calculations and limit comparisons
- Real-time monitoring capabilities

### CIRT Data Source
- Data source connectivity and reliability
- Proper data flow from upstream systems

### Alert Management
- Breach notification system
- Email distribution and formatting
- Acknowledgment workflow

## Test Evidence

The test documentation includes:

- LMS configuration screenshots
- Breach calculator execution logs
- Sample breach and no-breach email alerts
- Brisk report outputs
- End of day, control, and monthly report samples
- CIRT data source validation

## Environment Details

- **Testing Environment:** UAT (User Acceptance Testing)
- **Production System:** Brisk RRA Production Environment
- **Integration Points:** LMS, Brisk, CIRT, Email notification system

## Success Criteria Met

All breach and no-breach alerts generated successfully  
Brisk report data consistency verified  
Workflow integration completed without errors  
End of day reports functioning properly  
Control reports generated successfully  
Monthly reporting (Bob job) executed successfully  

## Dependencies

- LMS (Limit Management System)
- Brisk reporting platform
- CIRT data sources
- Email notification infrastructure
- VTD CFTC calculation engine

## Contact Information

For questions or issues related to this implementation:
- **Business Owner:** LOB (Line of Business) - Municipal Banking and Markets
- **Technical Contact:** [To be updated with appropriate team contact]
- **JIRA Reference:** FICCRISK-32258

## Notes

- Ensure proper coordination with LOB for measure details and filter specifications
- All testing performed in UAT environment before production deployment
- Regular monitoring of limit breaches and system performance recommended post-implementation
