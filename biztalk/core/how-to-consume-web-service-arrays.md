---
title: 如何使用 Web 服務陣列 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP adapters, Web services
- Web services, arrays
- orchestrations, Web services
- orchestrations, Web ports
ms.assetid: 29ecaaed-aa8a-4cf9-a7c8-4b0d6dd412ac
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e78f12405c9c331a888a268d39e2a1520c84fdc8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249894"
---
# <a name="how-to-consume-web-service-arrays"></a>如何使用 Web 服務陣列
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 讓您能夠從 [BizTalk 協調流程] 使用 Web 服務中公開的陣列。  
  
 **若要設定協調流程 使用 Web 服務中公開的陣列：**  
  
 決定公開陣列之 Web 服務的 URL。 通常是 asmx 網頁，其中列出 Web 服務支援的作業。 例如： http://localhost/ArrayWS/ArraySvc.asmx。  
  
1.  在包含協調流程的 Visual Studio 專案中新增此 URL 的 Web 參考：  
  
    -   在 [方案總管] 中，以滑鼠右鍵按一下**參考**，然後按一下**加入服務參考**。  
  
    -   在**加入服務參考**對話方塊中，按一下 **進階**。  
  
    -   在**服務參考設定**對話方塊中，按一下 **加入 Web 參考**中**相容性**> 一節。  
  
    -   在**加入 Web 參考**對話方塊方塊中，輸入 Web 服務的 URL **URL**文字方塊中，然後按一下**移**。  
  
    -   輸入 Web 參考到名稱**Web 參考名稱**文字方塊中，然後按一下**加入參考** 按鈕。  
  
    -   Web 參考會出現在**Web 參考**在 [方案總管] 中。  
  
        > [!TIP]
        >  將 Web 參考加入至專案中，一旦**加入 Web 參考**命令時，直接使用您以滑鼠右鍵按一下專案名稱或**參考**或**的Web參考**.  
  
2.  新增 Web 連接埠至協調流程：  
  
    -   拖曳**連接埠**圖形從工具箱拖曳至其中一個連接埠介面，以啟動協調流程設計師**連接埠組態精靈**。 按一下**下一步**按鈕**連接埠組態精靈**顯示**連接埠內容**對話方塊。  
  
    -   輸入值**名稱**文字方塊中，以找出連接埠，然後按一下**下一步** 按鈕以顯示**選取連接埠類型**對話方塊。  
  
    -   選取的選項**使用現有的連接埠類型**，選取 [Web 連接埠類型，對應至 Web 參考您加入，然後按一下**下一步**] 按鈕以顯示**連接埠繫結**對話方塊。  
  
    -   在**連接埠繫結**對話方塊中選取適當**連接埠繫結**選項，然後按一下**下一步**按鈕，然後按一下**完成**按鈕。 現在，包含 Web 服務支援之作業的 [協調流程設計師] 中應該會顯示 Web 連接埠。  
  
3.  新增**傳送**和**接收**到適當協調流程的圖形：  
  
    -   拖曳**傳送**圖形的連接線，設定讓協調流程將要求訊息傳送至 Web 連接埠協調流程設計師介面 中從 工具箱。 如果您連接**傳送**圖形以其中一個 Web 連接埠要求訊息連接器，BizTalk 將自動建立傳送要求訊息至此連接埠時所要使用的適當類型訊息。  
  
    -   拖曳**接收**圖形的連接線，設定讓協調流程從 Web 連接埠接收回應訊息的協調流程設計師介面 中從 工具箱。 如果您連接**接收**圖形至其中一個 Web 連接埠回應訊息連接器，BizTalk 將自動建立自此連接埠接收回應訊息時所要使用的適當類型訊息。  
  
> [!NOTE]
>  使用 SOAP 配接器傳送訊息至 Web 服務，或自 Web 服務接收訊息。 如需設定 SOAP 配接器的詳細資訊，請參閱[設定 SOAP 配接器](../core/configuring-the-soap-adapter.md)。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程引擎支援同時使用 Web 服務公開的一維和不規則陣列。 如果您新增公開陣列之 Web 服務的 Web 參考，則 [協調流程設計師] 將產生描述陣列的 Web 訊息類型。 然後您就可以傳送和接收此類型的訊息，就像接收其他訊息一般。 BizTalk Server 不會限制僅傳送包含陣列的 Web 訊息至 Web 連接埠。  
  
 如需使用 Web 服務陣列的範例，請參閱 SDK 範例 「 取用 Web 服務 」 和 「 取用 Web Services with Array Parameters"網址[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程中使用訊息](../core/using-messages-in-orchestrations.md)