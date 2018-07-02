---
title: 無效的控制標準識別項 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d2b5a54-7f29-49c9-8bcf-a5b4b6d07ad3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cadbb2ed9458199433b62ecb918668fda8a1def0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966231"
---
# <a name="invalid-control-standard-identifier"></a>無效的控制標準識別項
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                   X12Ta1InvalidControlStandardIdentifierDescription                    |
|  訊息文字   |                          無效的控制標準識別項                           |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換控制標準識別項 （欄位 ISA11） 交換中的值不符合列舉型別中的項目指定由結構描述。 結構描述是 x12serviceschema EdifactServiceSchema BaseArtifacts.dll 中。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定交換中使用的交換控制標準識別項符合 ISA11 欄位中，列舉型別中的項目，然後重新傳送交換。