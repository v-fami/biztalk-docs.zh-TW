---
title: "定義時間間隔和時間配量屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], aggregations
- managing [BAM], real-time data
- Primary Import database [BAM], time properties
- aggregations [BAM], managing
- Primary Import database [BAM], real-time data
- BAMConfiguration.xml file
- aggregations [BAM], real-time data
ms.assetid: 7f07b179-da10-4702-baf7-69516c8f16a6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d846b03866196e0a31facbbff68db50ec6a00a5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="defining-the-time-window-and-time-slice-properties"></a>定義時間間隔和時間配量屬性
系統管理員可以使用 BAMConfiguration.xml 檔案中的 TimeWindow 和 TimeSlice 屬性，定義 BAM 主要匯入資料庫之即時彙總資料表中資料的存留時間。  
  
> [!NOTE]
>  若要使系統管理員在 BAM 組態檔案中所做的變更生效，系統管理員必須解除部署目前的 BAM 組態，然後部署已更新的 BAMConfiguration.xml。  
  
 如需解除部署 BAM 定義，請參閱[如何移除 BAM 定義](../core/how-to-remove-bam-definitions.md)。 如需部署 BAM 定義的相關資訊，請參閱[如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md)。  
  
 如果您只要變更 TimeWindow 和 TimeSlice 值而不解除部署 BAM 基礎結構，則可修改 BAM 主要匯入資料庫的 BAM_Metadata_Activities 資料表中對應的資料行。  
  
## <a name="timeslice"></a>TimeSlice  
 請使用 TimeSlice 屬性將已完成的 BAM 執行個體資料分組。 TimeSlice 屬性根據資料寫入 BAM 主要匯入資料庫的時間，將 BAM 執行個體資料分組。  
  
 例如，執行個體 A 是完成和 BAM 主要匯入資料庫中保存在 1/1/2000年 1:02 a.m 是完成的執行個體 B，並將其保存在 BAM 主要匯入資料庫，在 1/1/2000年 1:04 a.m. 如果您設定 TimeSlice 屬性的值為 5 分鐘，執行個體 A 和 B 會群組在一起。  
  
#### <a name="to-change-the-timeslice-value-in-the-bam-configuration-file"></a>在 BAM 組態檔中變更 TimeSlice 值  
  
-   請變更 BAM 組態檔中這一行的值：  
  
    ```  
    <Property Name="RTATimeSlice">5</Property>  
    ```  
  
#### <a name="to-change-the-timeslice-value-in-the-bammetadataactivities-table"></a>在 BAM_Metadata_Activities 資料表中變更 TimeSlice 值  
  
-   請修改位於 BAMPrimaryImport 資料庫之 bam_Metadata_Activities 資料表中的 RTATimeSlice 值。 如果您針對一或多個活動部署多個即時彙總 (RTA)，便可選擇為每個 RTA 指定不同的時間間隔。  
  
    > [!NOTE]
    >  RTAWindow 的值必須是整數，且時間單位永遠為分鐘。  
  
## <a name="timewindow"></a>TimeWindow  
 當您執行 CubeUpdate DTS 封裝時，封裝會將資料從 BAM 主要匯入資料庫移至 BAM Cube。 一旦歸為同一群組的所有 BAM 資料執行個體都已超過 RTA 視窗屬性所指定的存留時間，封裝就會移動整組即時彙總資料。  
  
#### <a name="to-change-the-timewindow-value-in-the-bam-configuration-file"></a>在 BAM 組態檔中變更 TimeWindow 值  
  
-   請變更 BAM 組態檔中這一行的值：  
  
    ```  
    <Property Name="RTAWindow">60</Property>  
    ```  
  
#### <a name="to-change-the-timewindow-value-in-the-bammetadataactivities-table"></a>在 BAM_Metadata_Activities 資料表中變更 TimeWindow 值  
  
-   請修改位於 BAMPrimaryImport 資料庫之 bam_Metadata_Activities 資料表中的 RTAWindow 值。 如果您針對一或多個活動部署多個即時彙總 (RTA)，便可選擇為每個 RTA 指定不同的時間間隔。  
  
    > [!NOTE]
    >  RTAWindow 的值必須是整數，且時間單位永遠為分鐘。  
  
## <a name="see-also"></a>另請參閱  
 [BAM 組態結構描述](../core/bam-configuration-schema.md)   
 [BAM 安全性建議](../core/bam-security-recommendations.md)