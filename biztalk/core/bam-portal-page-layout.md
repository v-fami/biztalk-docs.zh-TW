---
title: "BAM 入口網站頁面版面配置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM portal
- Portal page [BAM portal]
ms.assetid: 0d8833b7-dd2f-475c-a890-e925ee47d219
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5569021698eb856d7584a2510a27d69f092f37a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-portal-page-layout"></a>BAM 入口網站頁面版面配置
BAM 入口網站頁面的版面配置使用下列三個框架：  
  
-   橫幅  
  
-   我的檢視  
  
-   內容  
  
## <a name="banner"></a>橫幅  
 **橫幅**框架橫跨在入口網站頁面的頂端。 [橫幅] 框架包含商標資訊，如公司名稱和標誌、該頁面使用者介面 (UI) 的 [說明] 連結以及頁面標題。 您可以依據組織的需求自訂商標資訊。 如需自訂橫幅中的商標資訊的詳細資訊，請參閱[自訂 BAM 入口網站組態](../core/customizing-the-bam-portal-configuration.md)。  
  
## <a name="my-views"></a>我的檢視  
 **我的檢視**框架是在入口網站頁面的左半部。 [我的檢視] 會顯示目前的使用者有權檢視的所有項目。 使用者可以展開任一檢視，以查看在該檢視下可使用的功能。 如果沒有顯示任何檢視，原因可能是因為尚未建立檢視 (通常是商務分析師的工作)，或尚未授與該使用者權限 (通常是系統管理員的工作)。  
  
 您可以在檢視中執行每個檢視所提供的三項工作：  
  
-   **活動搜尋**： 可讓您建立查詢和活動為基礎的警示。  
  
-   **彙總**： 可讓您檢視彙總資料，並依據樞紐分析圖中的總計建立警示。  
  
-   **警示管理員**： 可讓您建立、 編輯、 檢視和訂閱警示。  
  
> [!NOTE]
>  如果您從「我的檢視」框架選取 [警示管理員]，則只能編輯現有的警示。 若要建立新警示，您必須從 [活動搜尋] 或 [彙總] 頁面移至 [警示管理員] 頁面。  
  
## <a name="content"></a>內容  
 **內容**框架是在入口網站頁面的右側。 內容頁面上包含各項「我的檢視」工作 ([活動搜尋]、[彙總] 和 [警示管理]) 所呈現的資訊。 內容框架會隨著您選取的工作變更，以反映與該項工作相關聯的功能。  
  
## <a name="see-also"></a>另請參閱  
 [BAM 入口網站上的活動搜尋頁面](../core/activity-search-on-the-bam-portal-page.md)   
 [BAM 入口網站上的彙總頁面](../core/aggregations-on-the-bam-portal-page.md)   
 [BAM 入口網站上的警示管理員頁面](../core/alert-manager-on-the-bam-portal-page.md)   
 [BAM 入口網站](../core/bam-portal.md)