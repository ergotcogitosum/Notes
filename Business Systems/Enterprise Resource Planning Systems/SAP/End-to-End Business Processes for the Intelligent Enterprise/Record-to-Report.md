![[FI and CO Flows - Video - identifying-the-areas-of-financial-and-management-accounting_.png]]
# Accounting Definitions
![[FI vs CO Expenses and Income.png]]
## Financial Accounting(FI)
Financial Accounting itself consists of different areas: The General Ledger (G/L) and various subledgers. The goal of FI is to manage expenses and income.
![[FI - You are here diagram for BTP.png]]
## Managerial Accounting(CO)
Short for Controlling. Specifically accounting for the costs and revenues.

# Record-to-Report Process
## Creditworthiness
- Manage Credit Limits
## Master Data & Financial Transactions
### Manage G/L Accounting

#### Basic Data for Chart of Accounts
General Tab
- G/L Account Number
- Account Description (Long Name)
- Translation Information (Account Name in Other Languages)
Account Company Code Data Tab
- Controlling Area
- Company Code
Company Code Assignment Tab
- Control Data Tab
	- Account Currency
	- "Only Balance in Local Currency"
	- Reconciliation Account Type
		- K - Vendor
		- D - Customer
		- A - Assets
- Create/Bank/Interest Tab
	Additional controls for the behavior of the account can be found here. An Example is the "Post Automatically Only" field which controls whether an account can be use for manual posting transactions
#### Account Type
![[Account Type By Domain.png]]
##### Cash Account
G/L Accounts Range 10000000-39999999
- Balance Sheet Reporting for FI
- Manage all bank accounts via a single reconciliation
##### Balance Sheet Account
G/L Accounts Range 10000000-39999999
- Only used in reporting for the Balance Sheet
- Not relevant to CO
##### Non Operating Expense or Income
G/L Accounts Range 40000000-79999999
- Income Statement Account used by FI that reports revenues from activities that are not part of the main purpose of the company.
- Defined by a lack of cost or revenue elements (Non-Recurring Activities usually)
##### Primary Costs or Revenue
G/L Accounts Range 40000000-79999999
- Income Statement Account used by FI that tracts the primary operating costs
- Primary Costs will automatically generates the corresponding cost or revenue postings
##### Secondary Costs
G/L Accounts Range 90000000-99999999
- Result from value flows within the organization such as internal activity cost allocations, overhead allocations, and settlement transactions.
- Only used for CO
#### SAP G/L Accounts Default Configuration
	Default Account Grouping Headers for the YCOA (??? Chart of Accounts)
##### 1XXXXXXX
- Bank
- Petty Cash
- Fixed Asset Accounts
##### 2XXXXXXX
- Trade Payables
- Tax Accounts
- Accrued Net Payroll Accounts
##### 3XXXXXXX
- Share Capital Accounts
##### 4XXXXXXX
- Revenue
- Discount
- Deduction
##### 5XXXXXXX
- Material Consumption
- Inventory Change
##### 6XXXXXXX
- Travel Costs
- Payroll
- Operating Expense Accounts
##### 7XXXXXXX
- Interest
- Valuation Loss and Gain Accounts (Shareholder Equity)
- Tax Accounts
## Money
- Manage Payments
- Manage Disputes
#### G/L Account Master Data
##### GL Account

##### Cost Element Categories
- Maintained on the G/L Account Master Data>Controlling Data Tab
- Flag for whether this account is used in CO
- Dictated by the Account Type from the G/L Account Master Data>General Tab
- How it can be used and the balances can be transferred
![[Cost Element Categories.png]]
## Reporting

### General Journal Entry (Manual Journal Entry)
- Most Accounting Txns should automatically post to the correct accounts as a result of the account basic data configuration
- Occasional Manual Journal Entries are needed
#### Components of a Manual Journal Entry
- Document Header
	- Company Code
	- Total Balance
		Total Balance is displayed in the top right. Debit and Credits must be equal
	- Journal Entry Date: Day that document was issued (date of the original document or txn)
	- Posting Date: Day that document was registered in Financial Accounting
	- Journal Entry Type
		- KR - Vendor Invoice
		- ZP - Payment Posting
		- AA - Asset Posting
- Document Items
	- Account Number
		Filtered by the Company Code entered on the Document Header
	- Amount
	- Debit and Credit Assignments

### Business Partner
The Business Partner is the SAP term for a person or legal entity. These are maintained as master data on the client which is shared all users of the SAP ecosystem.

Company Code views of the Business Partners allow for specific configurations for localities like VAT's, payment methos, and banks.

## General Business Partner Configurations
- Customer
- Supplier
- FI Customer - Generates Accounts Receivables
- FI Vendor - Generates Accounts Payables
### Business Partner Basic Data
- Business Partner Category
	- Person
	- Organization
- Grouping
	- Externally
		- Defined Naming Schema
		- Keyed by the record keeper
	- Internally
		- Consecutive running ledger for the Grouping
- BP Role
	Template for the configuration of the business partner
	- FI Vendor
	- FI Customer
	
## Reconciliation Process
![[Reconciliation Account Diagram.png]]
![[Account Receivables Intro - Blank T Charts.png]]
### Managing Accounts Payable
- Company specific configurations for the following elements
		- Reconciliation Account
		- Payment Terms and Basic Data
### Manage Accounts Receivable
- Company specific configurations for the following elements
		- Reconciliation Account
		- Payment Terms
		- Dunning Terms
![[Managing Accounts Receivable.png]]
## Asset Accounting
Balance Sheet Categories
	- Intangible Assets
	- Fixed Assets
		Non-current asset accounts are usually subdivided into line items for the sake of balance sheet reporting
	- Financial Assets
		SAP's customization tool for financial instruments is the "Financial Risk & Treasury Software"
### Asset Lifecycle
#### Create Asset Master Record
##### Fixed Asset Master Record
Accounting Data
	- Asset  Class
		- Account
		- Control Parameters
		- Master Data Default Values
	- Depreciation Areas
		-These different valuation approaches are displayed using depreciation areas (and ledgers) in the asset master record. **For this reason, the control parameters and default values (see Asset Class) for the depreciation calculation are always displayed at the level of the depreciation area of an asset.**
General Master Data Requirements:
	- Asset Description
	- Account Information (Cost center, etc)
	- Posting Information (Activation Date)
	- Physical Inventory Data (Last Inventory Date)
	- Origin Data (Vendor, manufacturer)
Valuation Data
	- Depreciation Keys
	- Useful Life
	- Expired Useful Life
	- Starting Date of Depreciation
	- Scrap Value
#### Asset Acquisition
Posting Methods
- via Accounts Payable
	- Without Accounts Payable integration: The assets are posted either before the invoice is received or after the invoice is posted by the Accounts Payable department in a separate step.
	- With Accounts Payable integration: The assets and the incoming invoices are posted in one step.
- via Procurement
	- Posted during "Goods Receipt" as part of the Invoicing Process
Capitalization
	Capitalization is determined during the Acquisition Process.
	- Capitalization date controls the posting of the transactions and when the depreciation started.
#### Asset Accounting and Depreciation
- **Ordinary depreciation (Straight Line)** represents the planned depreciation of an asset when the asset is normally used. Ordinary depreciation reflects the deduction for wear and tear during the normal use of the asset.
- **Unplanned depreciation** covers unusual influences that lead to a permanent decrease in the value of an asset. For example, damage of a production machine.
- **Special depreciation** is a depreciation for wear and tear that is based solely on tax law. This type of depreciation allows you to depreciate a percentage of the asset value. The percentage rate can be scaled within a tax concession period, without taking into account the actual wear and tear of the asset.
#### Asset Retirement
- Sale
	- Posts to a clearing account
	- Integrated with AR
- Scrapping
## Ledgers for Parallel Accounting
[Parallel Accounting | SAP Help Portal](https://help.sap.com/docs/SAP_S4HANA_CLOUD/6b39bd1d0e5e4099a5b65d835c29c696/fce0d25320cd4608e10000000a174cb4.html)

## Processing Plan and Actual Data in Overhead Cost Controlling
Material Costs +
Production Costs
______________
= Cost of Goods Manufactured
+
Sales Costs and Administrative Overhead Costs
______________________
= Cost of Goods Sold
### Cost Center Master Data
- Cost centers define areas of responsibility within the company that collect overhead costs
- Secondary Cost Accounts
	Secondary cost elements are only posted in Management Accounting (CO). These accounts are designated with the account type "Secondary Costs"
- Activity Types
	Activity Types exist so that work centers can transfer types and keep track of them against the overhead.
	Inter-cost center activities are managed via the WBS or other cost centers
	- Price Indicator
		Cost to be billed in the system
	- Allocation Cost Element
		Secondary Cost Element account for CO
- Plan Price
	Activity Costs can be variable or fixed
### Profit Planning
	Final step of the Sales and Operations planning cycle where projections are measured against the benchmarks of the enterpise. This is the feedback cycle for the S&OP planning cycle.


![[Cost Center Master Data Hierarchy.png]]
![[Secondary Cost Account Structure.png]]
### Work Breakdown Structure (WBS elements)