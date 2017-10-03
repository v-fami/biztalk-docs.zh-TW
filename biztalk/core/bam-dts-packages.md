---
title: "BAM DTS 封裝 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DTS packages, BAM
- BAM, DTS packages
ms.assetid: bba70d81-6ddf-4f1f-a1f7-d5a5bf453bae
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 105d1b42848b73505d9a82df07693111708ce802
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-dts-packages"></a>BAM DTS 封裝
系統管理員可以更新下列 BAM DTS 封裝的參數：  
  
-   **CubeUpdate** Data Transformation Services (DTS) 封裝永遠位於與星狀結構描述資料庫相同的伺服器。  
  
-   **DataMaintenance** DTS 封裝永遠位於主要匯入資料庫與相同的伺服器。  
  
 DTS 封裝在 BAMConfiguration.xml 檔案中使用下列參數。  
  
|參數|Description|  
|---------------|-----------------|  
|ConnectionTimeOut|DTS 連線逾時值 (以秒為單位) 是整數。 如果省略 ConnectionTimeOut 參數，組態檔案就會使用 60 秒 (預設值)。|  
|加密|DTS 封裝轉換資料時，預設不會加密資料 (Encryption 值為 0)。 將 Encryption 設定為 1，即可在轉換期間加密資料。|  
|OwnerPassword|DTS 封裝擁有者的密碼。 DTS 封裝擁有者可以開啟和修改 DTS 封裝。 如需 DTS 封裝擁有者的詳細資訊，請參閱《SQL Server 線上叢書》。|  
|UserPassword|DTS 使用者的密碼。 DTS 封裝使用者可以執行 DTS 封裝。 如需 DTS 封裝使用者的詳細資訊，請參閱《SQL Server 線上叢書》。|  
  
 DTS 封裝在 BAMConfiguration.xml 檔案中使用下列命名慣例：  
  
-   **CubeUpdate** DTS 封裝  
  
     **bam_AN_\<**   
     ***CubeName* >**，其中 CubeName 是 cube 的名稱。 BAM 活頁簿會從檢視名稱產生 Cube 的名稱。 如果您修改 BAM 組態 XML 文件中的 Cube 名稱，DTS 封裝名稱就會使用新的 Cube 名稱。  
  
-   **DataMaintenance** DTS 封裝  
  
     **bam_DM_\<**   
     ***ActivityName* >**，其中 ActivityName 是活動的名稱。  
  
 執行 CubeUpdate DTS 封裝，可以彙總已排程的彙總。 在下一節中，您將會指定即時資料彙總的時間間隔。  
  
## <a name="see-also"></a>另請參閱  
 [BAM 組態結構描述](../core/bam-configuration-schema.md)   
 [BAM 安全性建議](../core/bam-security-recommendations.md)   
 [管理 BAM](../core/managing-bam.md)