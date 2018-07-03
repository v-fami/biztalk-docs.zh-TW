---
title: 結構描述區段應該依照下列順序 ST...SE |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f4d1c6a-7d48-413a-9ef5-a0c49773dc16
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c98bc756e4bd75a8a15111c54f433a7f9c6c0509
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015167"
---
# <a name="schema-should-have-segments-in-the-following-order-st--se"></a>結構描述區段應該依照下列順序 ST...SE
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                    SchemaCode116ETransactionSetSchemaStSeOutOfOrder                    |
|  訊息文字   |             結構描述區段應該依照下列順序 ST...SE              |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示自訂文件結構描述不正確的因為標頭和結尾不是處於正確的順序。 部署結構描述時，BizTalk Server 會執行這項驗證。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請變更自訂文件結構描述，以便標頭和結尾會以正確的順序，並重新部署結構描述。