---
title: 找不到 CLR 命名空間和 rootName 的結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db283d81-1cb0-460d-ace4-49a91ceb4a02
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a830d46a439ad85e5e9e3d54afaca688dac201ca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966343"
---
# <a name="schema-not-found-for-clr-namespace-and-rootname"></a>找不到 CLR 命名空間和 rootName 的結構描述
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                               SchemaNotFoundForCLRAndRN                                |
|  訊息文字   |              找不到 CLR 命名空間的結構描述 ={0}和 rootName = {1}               |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線找不到使用與交換關聯的根名稱和已解決之交換的合作對象相關聯的命名空間的文件結構描述。  
  
## <a name="user-action"></a>使用者動作  
 若要解決此錯誤，確定從交換採用的根目錄名稱與根據已解析合作對象之屬性決定的命名空間都對應部署的結構描述。 BizTalk 根據交換的文件類型和版本判斷根目錄名稱。 BizTalk 根據 [預設目標命名空間] 欄位 (針對預設結構描述)，或交換處理屬性中的 [啟用自訂交易集定義] 方格 (針對自訂結構描述)，判斷結構描述。