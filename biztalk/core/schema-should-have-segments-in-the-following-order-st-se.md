---
title: "結構描述應該有下列順序 ST 區段...SE |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f4d1c6a-7d48-413a-9ef5-a0c49773dc16
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2563247dc6fc4c092fe2867c6b4d03239c4be7e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schema-should-have-segments-in-the-following-order-st--se"></a>結構描述應該有下列順序 ST 區段...SE
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|SchemaCode116ETransactionSetSchemaStSeOutOfOrder|  
|訊息文字|結構描述應該有下列順序 ST 區段...SE|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示自訂文件結構描述不正確的因為標頭和結尾未以正確的順序。 部署結構描述時，BizTalk Server 會執行這項驗證。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，變更的自訂文件結構描述，以便與標頭和結尾的正確順序，然後重新部署結構描述。