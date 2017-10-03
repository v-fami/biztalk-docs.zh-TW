---
title: "中繼資料錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccb60c91-5905-4852-813b-586b82de4825
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dce5fc9eb944eccbeed57073c2546f81825ec6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-errors"></a>中繼資料錯誤
診斷及解決 WCF 中繼資料錯誤的資訊。  
  
## <a name="error-consuming-wcf-service-metadata"></a>取用 WCF 服務中繼資料時發生錯誤

||錯誤詳細資料|  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|取用 WCF 服務中繼資料時發生錯誤|  
  
### <a name="explanation"></a>說明  
 此錯誤表示中繼資料可供服務未使用或不正確。  
  
### <a name="user-action"></a>使用者動作  
 更正服務中繼資料，並嘗試使用 （如果您擁有想要使用的 WCF 服務）。 移至服務組態編輯器 (**svcConfigEditor.exe**) 並對組態檔進行變更。  否則，請連絡服務提供者

## <a name="failed-to-get-metadata"></a>無法取得中繼資料

||錯誤詳細資料|  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無法從 "{0}" 取得中繼資料|  
  
## <a name="explanation"></a>說明  
 此錯誤表示沒有可供該服務的中繼資料。  
  
## <a name="user-action"></a>使用者動作  
 啟用服務的中繼資料，然後再次執行使用精靈，（如果您擁有想要使用的 WCF 服務）。 否則，請連絡服務提供者。