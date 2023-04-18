# Azure Workbooks

## Azure Hybrid Benefit Tracking Dashboard

### What is Azure Hybrid Benefit?

Azure Hybrid Benefit is a licensing benefit that allows you to bring your on-premises core-based Windows Server, SQL Server, and Red Hat Linux licenses with active Software Assurance (or subscription) to Azure. Utilizing this benefit can save considerable cost by eliminating the hourly licensing charges for Azure resources, allowing you to pay only for hardware resources. By leveraging Azure Hybrid Benefit, you can optimize your cloud infrastructure costs.

### Keeping track of Azure Hybrid Benefit Usage

Managing and keeping track of Azure Hybrid Benefit entitlements can be challenging however, especially for organizations with a large number of licenses and virtual machines. Ensuring that you are utilizing your entitlements effectively while maintaining compliance with licensing agreements requires careful monitoring and management. It is essential to have a clear understanding of your organization's licensing landscape and to establish processes for tracking and applying Azure Hybrid Benefit entitlements.

I've created this Workbook to simplify the management of Azure Hybrid Benefit in your environment. Azure Workbooks provide a flexible, interactive, and customizable way to visualize and analyze your Azure resources. By querying the Azure Resource Graph, the report gathers real-time information about your virtual machines' usage of Azure Hybrid Benefit and creates visualizations to help you understand your licensing landscape.

![Dashboard example image](https://github.com/rlowellfl/azure_workbooks/blob/c2912589d537caea89aa5dca293b799009a53c78/media/ahb_dashboard_example.png)

### Getting started

You can get started with the Dashboard by clicking the following link:

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Frlowellfl%2Fazure_workbooks%2Fmain%2Fhybrid_benefit_tracker_workbook.json)

1. Select your preferred Subscription, Resource Group, and Region to store the dashboard resource. Leave all other fields as-is.
2. Once the resource is created, open the Dashboard.
3. Fill in the AHB Entitlement field in the upper left corner with the number of Azure Hybrid Benefit cores which your organization is entitled to.
4. The workbook will then use the Azure Resource Graph to query all Windows Server virtual machines and display your total virtual machine cores, AHB cores utilized, and AHB cores available.
5. The workbook will also analyze whether a virtual machine is an optimal use of Azure Hybrid Benefit, as machines with less than 8 vCPUs still consume a minimum of 8 Azure Hybrid Benefit cores.

Please note the following important points when using this tool:

* This dashboard currently only provides information on Windows Server utilization. SQL Server on Azure VMs, SQL Managed Instance, Azure SQL, and Red Hat Linux are not included in this report. Keep an eye on this repository for future updates and additional views.
* The charts and resources below are based on the Virtual Machines which your user account has RBAC access to view. Virtual machines in other tenants, management groups, subscriptions, or resource groups which are not visibile to you will not be calaculated and the totals above may be inaccurate. Please ensure that your organization remains in compliance with all license terms and conditions for Azure Hybrid Benefit.