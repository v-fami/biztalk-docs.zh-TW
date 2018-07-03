---
title: 無效的時間 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6942eb77-3ef1-460c-ac4f-8f1339c25d1b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 555934e0be188011a69efb3966e5316bc716c254
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023820"
---
# <a name="invalid-time"></a>無效的時間
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                              X12Ta1InvalidTimeDescription                              |
|  訊息文字   |                                      無效的時間                                      |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 EDI 結構描述或 GS05 欄位標頭在 X12 中的時間值所指定的資料類型不符合資料元素中的時間值服務結構描述不符合交換 (BaseArtifacts.dll 中的 X12ServiceSchema)。 對於 X12，服務結構描述會定義一次在 GS05 欄位截至 X12_TM 資料類型和長度為四到八個字元之間。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定時間，資料元素中的值符合 EDI 結構描述或 X12 服務結構描述符合交換的 GS05 標頭中的時間值所指定的資料類型，並再重新傳送交換。