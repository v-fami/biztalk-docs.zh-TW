---
title: 如何顯示監視閾值 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 88d88b15-0691-49d9-b116-1a2ae95bead9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be3818512f76e95655e0441f039176fe6f855344
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297702"
---
# <a name="how-to-display-monitor-thresholds"></a><span data-ttu-id="408ca-102">如何顯示監視閾值</span><span class="sxs-lookup"><span data-stu-id="408ca-102">How to Display Monitor Thresholds</span></span>
<span data-ttu-id="408ca-103">若要顯示監視閾值，請使用本節中所述的指令碼。</span><span class="sxs-lookup"><span data-stu-id="408ca-103">To display monitor thresholds, use the script described in this section.</span></span> <span data-ttu-id="408ca-104">此指令碼適用於大部分監視。</span><span class="sxs-lookup"><span data-stu-id="408ca-104">This script works for the majority of monitors.</span></span> <span data-ttu-id="408ca-105">它會建立.csv 檔案，其中包含下表中描述的資料行，並且可以使用 Office Excel 加以檢視。</span><span class="sxs-lookup"><span data-stu-id="408ca-105">It creates a .csv file that includes the columns described in the following table, and can be viewed using Office Excel.</span></span>  
  
|<span data-ttu-id="408ca-106">資料行</span><span class="sxs-lookup"><span data-stu-id="408ca-106">Column</span></span>|<span data-ttu-id="408ca-107">說明</span><span class="sxs-lookup"><span data-stu-id="408ca-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="408ca-108">類型</span><span class="sxs-lookup"><span data-stu-id="408ca-108">Type</span></span>|<span data-ttu-id="408ca-109">監視的目標的物件的類型。</span><span class="sxs-lookup"><span data-stu-id="408ca-109">The type of objects the monitor is targeted.</span></span>|  
|<span data-ttu-id="408ca-110">DisplayName</span><span class="sxs-lookup"><span data-stu-id="408ca-110">DisplayName</span></span>|<span data-ttu-id="408ca-111">監視器的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="408ca-111">The display name of the monitor.</span></span>|  
|<span data-ttu-id="408ca-112">閾值</span><span class="sxs-lookup"><span data-stu-id="408ca-112">Threshold</span></span>|<span data-ttu-id="408ca-113">使用監視的閾值。</span><span class="sxs-lookup"><span data-stu-id="408ca-113">The threshold used by the monitor.</span></span>|  
|<span data-ttu-id="408ca-114">AlertOnState</span><span class="sxs-lookup"><span data-stu-id="408ca-114">AlertOnState</span></span>|<span data-ttu-id="408ca-115">決定是否此監視產生警示的狀態變更時。</span><span class="sxs-lookup"><span data-stu-id="408ca-115">Determines whether the monitor generates an alert when the state changes.</span></span>|  
|<span data-ttu-id="408ca-116">AutoResolveAlert</span><span class="sxs-lookup"><span data-stu-id="408ca-116">AutoResolveAlert</span></span>|<span data-ttu-id="408ca-117">決定是否產生的警示時，會自動解決監視狀態恢復綠色。</span><span class="sxs-lookup"><span data-stu-id="408ca-117">Determines whether the generated alert will be automatically resolved when the monitor state goes back to green.</span></span>|  
|<span data-ttu-id="408ca-118">AlertSeverity</span><span class="sxs-lookup"><span data-stu-id="408ca-118">AlertSeverity</span></span>|<span data-ttu-id="408ca-119">產生警示的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="408ca-119">The severity of the generated alert.</span></span>|  
  
#### <a name="to-display-monitor-thresholds"></a><span data-ttu-id="408ca-120">若要顯示監視閾值</span><span class="sxs-lookup"><span data-stu-id="408ca-120">To display monitor thresholds</span></span>  
 <span data-ttu-id="408ca-121">執行下列指令碼，以建立顯示監視閾值的.csv 檔案：</span><span class="sxs-lookup"><span data-stu-id="408ca-121">Run the following script to create the .csv file that displays the monitor thresholds:</span></span>  
  
```  
function GetThreshold ([String] $configuration)   
{   
  $config = [xml] ("<config>" + $configuration + "</config>")   
  $threshold = $config.Config.Threshold   
  if($threshold -eq $null)   
  {   
    $threshold = $config.Config.MemoryThreshold   
  }   
  if($threshold -eq $null)   
  {   
    $threshold = $config.Config.CPUPercentageThreshold   
  }   
  if($threshold -eq $null)   
  {   
    if($config.Config.Threshold1 -ne $null -and $config.Config.Threshold2 -ne $null)   
    {   
      $threshold = "first threshold is: " + $config.Config.Threshold1 + " second threshold is: " + $config.Config.Threshold2   
    }   
  }   
  if($threshold -eq $null)   
  {   
    if($config.Config.ThresholdWarnSec -ne $null -and $config.Config.ThresholdErrorSec -ne $null)   
    {   
      $threshold = "warning threshold is: " + $config.Config.ThresholdWarnSec + " error threshold is: " + $config.Config.ThresholdErrorSec   
    }   
  }   
  if($threshold -eq $null)   
  {   
    if($config.Config.LearningAndBaseliningSettings -ne $null)   
    {   
      $threshold = "no threshold (baseline monitor)"   
    }   
  }   
  return $threshold   
}   
#$perfMonitors = get-monitor -Criteria:"IsUnitMonitor=1 and Category='PerformanceHealth'"   
$perfMonitors = Get-ScommanagementPack -DisplayName "BizTalk Server Monitoring" | get-scommonitor | where-object{$_.XmlTag -eq "UnitMonitor" -and $_.Category -eq "PerformanceHealth"}  
  
$perfMonitors | select-object @{name="Target";expression={foreach-object {(Get-SCOMClass -Id:$_.Target.Id).DisplayName}}},DisplayName, @{name="Threshold";expression={foreach-object {GetThreshold $_.Configuration}}}, @{name="AlertOnState";expression={foreach-object {$_.AlertSettings.AlertOnState}}}, @{name="AutoResolveAlert";expression={foreach-object {$_.AlertSettings.AutoResolve}}}, @{name="AlertSeverity";expression={foreach-object {$_.AlertSettings.AlertSeverity}}} | sort Target, DisplayName | export-csv "c:\monitor_thresholds.csv"  
  
```