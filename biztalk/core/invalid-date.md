---
title: 無效的日期 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41da9c5-9dcf-44cd-be5b-922e6c267ec3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a7e5f8003cbb8cc88487f471e10ce0d7ba857e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987751"
---
# <a name="invalid-date"></a>無效的日期
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                              X12DeInvalidDateDescription                               |
|  訊息文字   |                                      無效的日期                                      |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，或傳送管線無法處理外寄交換，因為資料元素中的日期值不符合所指定之資料類型EDI 結構描述或 GS04 欄位標頭中 X12 服務結構描述不符合交換的日期值 (BaseArtifacts.dll 中的 X12ServiceSchema)。 對於 X12，服務結構描述會定義日期，在 GS04 欄位截至 X12_DT 資料類型和長度為六到八個字元之間。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定符合資料元素中的值時間為 EDI 結構描述或 X12 服務結構描述符合交換的 GS04 標頭中的日期值所指定的資料類型，並再重新傳送交換。