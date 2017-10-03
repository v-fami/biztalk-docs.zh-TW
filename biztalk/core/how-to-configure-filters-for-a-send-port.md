---
title: "如何設定傳送埠的篩選器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters, configuring
- filters, send ports
- configuring, filters
- managing [send ports], configuring
- send ports, configuring
- send ports, filters
- managing [send ports], filters
ms.assetid: ad13ca8e-bb1d-4449-8163-49dd9d5d92f8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7845b6189f86054ba9661ea450575a2dcfe47953
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-filters-for-a-send-port"></a>如何設定傳送埠的篩選
本主題說明如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定傳送埠的篩選條件。 您可以使用篩選來建立簡單的傳訊或以內容為基礎的路由 (Content-Based Routing，CBR) 應用程式。 篩選會設定訊息屬性或欄位的條件，以決定哪些訊息要路由至傳送埠。 篩選不會篩選協調流程路由至傳送埠的訊息。  
  
 您可以使用運算子，建立一個或多個由訊息屬性、運算子以及依屬性驗證的值所組成的篩選條件運算式。  
  
 例如，您可能建立如下的運算式：  
  
 MSMQ.MsgID = 1  
  
 依照這個篩選條件，傳送埠群組將只能訂閱 MSMQ 訊息識別碼為 1 的訊息。  
  
 您可以建立額外的運算式，並指定這些運算式與其他運算式之間有 AND 或 OR 關係，例如：  
  
 MSMQ.MsgID = 1 OR  
  
 SMTP.From = MyServer  
  
 在此例中，傳送埠群組將會訂閱 MSMQ 訊息識別碼為 1 的或從名為 MyServer 的 SMTP 伺服器所傳送的所有訊息。  
  
> [!NOTE]
>  如果您在一個使用其他應用程式中之屬性結構描述的應用程式內建立傳送埠的篩選，然後再將此應用程式匯入至新的 BizTalk 群組，那麼您在安裝及啟動應用程式時，將不會收到結構描述遺失的警告，並且篩選功能也無法運作。 在安裝沒有包含結構描述的應用程式之前，您可以先匯入包含結構描述的應用程式來修正問題。  
  
> [!NOTE]
>  應用程式開發人員可以使用此主題中的程序，在開發程序中設定傳送埠的篩選。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-filters-for-a-send-port"></a>設定傳送埠的篩選  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要為其設定傳送埠篩選的 BizTalk 群組與 BizTalk 應用程式。  
  
3.  展開**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下 **篩選**。  
  
4.  下表中所述，設定篩選器，然後按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**Delete**|按一下以刪除選取的篩選條件運算式。|  
    |**上移**|按一下以將篩選條件運算式序列中選取的屬性往上移。|  
    |**下移**|按一下以將篩選條件運算式序列中選取的屬性往下移。|  
    |**屬性**|在清單中按一下要在此篩選運算式中使用的訊息屬性。|  
    |**運算子**|輸入或選取運算式的運算子。|  
    |**值**|輸入值以驗證屬性。 接受的值類型依屬性類型的不同而不同。 若要查看某個屬性接受的值類型，請將滑鼠停留在該屬性上方。 可接受的值如下：Int: (Integer) 這必須是整數值。 String：字元字串。 dateTime：以 .NET 支援的格式表示的日期和 (或) 時間。 如需有關 .NET 所支援的時間格式詳細資訊，請參閱「.NET Frameworks 說明」中的＜DateTimeFormatInfo 類別＞。|  
    |**群組依據**|選取**和**或**或**來表示這與篩選條件運算式彼此之間的關聯性。|  
  
## <a name="see-also"></a>另請參閱  
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)