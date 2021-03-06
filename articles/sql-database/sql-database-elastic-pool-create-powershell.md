---
title: Create an new elastic pool with PowerShell | Microsoft Docs
description: Learn how to use PowerShell to scale-out Azure SQL Database resources by creating a scalable elastic pool to manage multiple databases.
services: sql-database
documentationcenter: ''
author: srinia
manager: jhubbard
editor: ''

ms.assetid: 37a707ee-9223-43ae-8c35-1ccafde8b83e
ms.service: sql-database
ms.custom: multiple databases
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: powershell
ms.workload: data-management
ms.date: 05/27/2016
ms.author: srinia

---
# Create a new elastic pool with PowerShell
> [!div class="op_single_selector"]
> * [Azure portal](sql-database-elastic-pool-create-portal.md)
> * [PowerShell](sql-database-elastic-pool-create-powershell.md)
> * [C#](sql-database-elastic-pool-create-csharp.md)
>
>

Learn how to create an [elastic pool](sql-database-elastic-pool.md) using PowerShell cmdlets.

For common error codes, see [SQL error codes for SQL Database client applications: Database connection error and other issues](sql-database-develop-error-messages.md).

> [!NOTE]
> Elastic pools are generally available (GA) in all Azure regions except North Central US and West India where it is currently in preview.  GA of elastic pools in these regions will be provided as soon as possible. Also, elastic pools do not currently support databases using [in-memory OLTP or in-memory analytics](sql-database-in-memory.md).
>
>

You need to be running Azure PowerShell 1.0 or higher. For detailed information, see [How to install and configure Azure PowerShell](/powershell/azureps-cmdlets-docs).

## Create a new pool
The [New-AzureRmSqlElasticPool](https://msdn.microsoft.com/library/azure/mt619378\(v=azure.300\).aspx) cmdlet creates a new pool. The values for eDTU per pool, min, and max Dtus are constrained by the service tier value (basic, standard, or premium). See [eDTU and storage limits for elastic pools and elastic databases](sql-database-elastic-pool.md#edtu-and-storage-limits-for-elastic-pools).

    New-AzureRmSqlElasticPool -ResourceGroupName "resourcegroup1" -ServerName "server1" -ElasticPoolName "elasticpool1" -Edition "Standard" -Dtu 400 -DatabaseDtuMin 10 -DatabaseDtuMax 100


## Create a new elastic database in a pool
Use the [New-AzureRmSqlDatabase](https://msdn.microsoft.com/library/azure/mt619339\(v=azure.300\).aspx) cmdlet and set the **ElasticPoolName** parameter to the target pool. To move an existing database into a pool, see [Move a database into an elastic pool](sql-database-elastic-pool-manage-powershell.md#move-a-database-into-an-elastic-pool).

    New-AzureRmSqlDatabase -ResourceGroupName "resourcegroup1" -ServerName "server1" -DatabaseName "database1" -ElasticPoolName "elasticpool1"

## Create a pool and populate it with multiple new databases
Creation of a large number of databases in a pool can take time when done using the portal or PowerShell cmdlets that create only a single database at a time. To automate creation into a new pool, see [CreateOrUpdateElasticPoolAndPopulate ](https://gist.github.com/billgib/d80c7687b17355d3c2ec8042323819ae).   

## Example: create a pool using PowerShell
This script creates a new Azure resource group and a new server. When prompted, supply an administrator username and password for the new server (not your Azure credentials).

    $subscriptionId = '<your Azure subscription id>'
    $resourceGroupName = '<resource group name>'
    $location = '<datacenter location>'
    $serverName = '<server name>'
    $poolName = '<pool name>'
    $databaseName = '<database name>'

    Login-AzureRmAccount
    Set-AzureRmContext -SubscriptionId $subscriptionId

    New-AzureRmResourceGroup -Name $resourceGroupName -Location $location
    New-AzureRmSqlServer -ResourceGroupName $resourceGroupName -ServerName $serverName -Location $location -ServerVersion "12.0"
    New-AzureRmSqlServerFirewallRule -ResourceGroupName $resourceGroupName -ServerName $serverName -FirewallRuleName "rule1" -StartIpAddress "192.168.0.198" -EndIpAddress "192.168.0.199"

    New-AzureRmSqlElasticPool -ResourceGroupName $resourceGroupName -ServerName $serverName -ElasticPoolName $poolName -Edition "Standard" -Dtu 400 -DatabaseDtuMin 10 -DatabaseDtuMax 100

    New-AzureRmSqlDatabase -ResourceGroupName $resourceGroupName -ServerName $serverName -DatabaseName $databaseName -ElasticPoolName $poolName -MaxSizeBytes 10GB



## Next steps
* [Manage your pool](sql-database-elastic-pool-manage-powershell.md)
* [Create elastic jobs](sql-database-elastic-jobs-overview.md) Elastic jobs let you run T-SQL scripts against any number of databases in the pool.
* [Scale out with Azure SQL Database](sql-database-elastic-scale-introduction.md): Use elastic database tools to scale-out.
