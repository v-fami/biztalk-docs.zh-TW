---
title: 載入組件的錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 600973e0-3142-455f-9afa-74430af31e38
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df561b964faa0fae80f41f1423d3034466bbb8ce
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994951"
---
# <a name="error-loading-assembly"></a>載入組件時發生錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                                                                                                      |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                                                                          |
| 產品版本 |                                                                                                                                                      [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                                                                                      |
|    事件識別碼     |                                                                                                                                                                                  0                                                                                                                                                                                   |
|  事件來源   |                                                                                                                                                                                  0                                                                                                                                                                                   |
|    元件    |                                                                                                                                                                                  0                                                                                                                                                                                   |
|  符號名稱  |                                                                                                                                                                                  0                                                                                                                                                                                   |
|  訊息文字   | 此錯誤表示位置是否在網路共用上，可能無法完全信任。 檢查該區域的程式碼存取安全性原則。 或者檔案可能不是 BizTalk.NET 組件。 檢查的組件 [組件： BizTalkAssembly] 自訂屬性。 或者檔案可能不是.NET 組件。 如果檔案是.dll 或 exe，可能是 unmanaged 程式碼 |
  
## <a name="explanation"></a>說明  
 此錯誤表示位置是否在網路共用上，可能無法完全信任。 檢查該區域的程式碼存取安全性原則。 或者檔案可能不是 BizTalk.NET 組件。 檢查的組件 [*組件： BizTalkAssembly*] 自訂屬性。 或者檔案可能不是.NET 組件。 如果檔案是.dll 或 exe，它可能是 unmanaged 程式碼。  
  
## <a name="user-action"></a>使用者動作  
 授與完整信任層級，如果它是來自可靠來源的位置。  請確定 dll 是有效的 BizTalk.net 組件。