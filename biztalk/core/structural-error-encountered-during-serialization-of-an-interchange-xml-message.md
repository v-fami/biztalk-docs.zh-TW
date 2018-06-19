---
title: 交換 XML 訊息的序列化期間遇到的錯誤結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 97939bfd-d1ee-455a-9952-4f25db020e7c
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44b56cce9fdd3704f7e6ddc2ba5b5bebb62d36e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278590"
---
# <a name="structural-error-encountered-during-serialization-of-an-interchange-xml-message"></a>結構化交換 XML 訊息的序列化期間遇到的錯誤
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|InvalidXmlNodeFound|  
|訊息文字|結構化交換 Xml 訊息的序列化期間遇到的錯誤|  
  
## <a name="explanation"></a>說明  
 此錯誤表示交換 XML 訊息的序列化期間遇到到結構的錯誤。 BTS 找出 XML StartElement 或 EndElement，但改為遇到不同的 XML 節點類型。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定訊息結構正確，並再試一次：  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後按一下**BizTalk 群組**。  
  
3.  在右窗格中，按一下 [**群組中樞**] 索引標籤。  
  
4.  按一下**擱置服務執行個體**。  
  
5.  按兩下的訊息。  
  
6.  在**服務詳細資料**視窗中，按一下 [**訊息**] 索引標籤。  
  
7.  按兩下訊息一次。  
  
8.  在左窗格中，按一下 **訊息部分 / b**。  
  
9. 判斷訊息結構是否正確。