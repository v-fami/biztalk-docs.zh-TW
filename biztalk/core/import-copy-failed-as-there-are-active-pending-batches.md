---
title: 匯入複製失敗，因為有作用-擱置中的批次 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17803f0a-3c70-4a8a-8e8d-7f874ed9ad92
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a74bfdccbd12db00cd0f325aedee2e42cc76729
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970535"
---
# <a name="import-copy-failed-as-there-are-active-pending-batches"></a>匯入複製失敗，因為有作用-擱置中的批次
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------|
|  產品名稱   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| 產品版本 |                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                           |
|    事件識別碼     |                                                       -                                                        |
|  事件來源   |             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI             |
|    元件    |                                                   將 EDI 引擎                                                   |
|  符號名稱  |                                              Err_ActiveBatchFound                                              |
|  訊息文字   | 匯入/複製失敗，因為有作用中/擱置中的批次。 停止作用中/擱置中的批次，然後再次嘗試匯入/複製。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法匯入繫結檔案，或複製的設定，受影響的合約具有一或多個作用中或擱置中的批次。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定在受影響的協議中的所有批次會顯示為協議屬性中已停止。