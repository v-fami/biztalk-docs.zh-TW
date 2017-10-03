---
title: "如何建立接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.procedure.createreceivelocation
helpviewer_keywords:
- receive locations, creating
- managing [receive locations], creating
- creating, receive locations
ms.assetid: ec0202cf-0e69-4ae2-aba6-8cd2c3c77e82
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe82afdc62a7ba2c10087c78a6a24c1722e5812a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-receive-location"></a>如何建立接收位置
本主題描述如何使用 BizTalk Server 管理主控台建立新的接收位置，並指定該位置所屬的接收埠。 接收位置是輸入訊息送達的位址，也是處理在該位址所接收之訊息的傳訊管線。  
  
 在建立接收位置之前，在這個應用程式中必須已經有接收埠存在 (該應用程式的類型要與所建立之接收位置相同)。 如需建立接收埠的指示，請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
 您可以建立下列類型的接收位置：  
  
-   單向：用在應用程式放置訊息但不同步等候回覆時  
  
-   要求-回應：用在應用程式需要訊息的回應時  
  
> [!NOTE]
>  應用程式開發人員可以使用此主題中的程序，在開發程序中建立接收位置。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。 此外，您必須擁有適當的 SSO 資料庫權限。  
  
### <a name="to-create-a-receive-location"></a>建立接收位置  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要建立其接收位置的 BizTalk 群組和 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**或**要求回應接收位置**根據的接收位置類型來建立。  
  
4.  在 選取接收埠 視窗中，按一下 接收埠，將會包含此接收位置，然後按一下**確定**。  
  
5.  在**接收位置屬性**視窗中，執行下列命令，，然後按一下**確定**:  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|輸入接收位置的名稱。|  
    |**型別**|從下拉式清單選取傳輸類型或傳輸通訊協定。 若您變更傳輸類型，則必須設定如下所描述的傳輸屬性。|  
    |**設定**|選取傳輸類型之後，請按一下**設定**顯示**傳輸屬性**對話方塊設定配接器接收位置屬性。 如需指示，請按一下**協助**在對話方塊中。 如需設定配接器，每種類型的詳細資訊，請參閱底下的適當主題[使用配接器](../core/using-adapters.md)。|  
    |**接收處理常式**|從下拉式清單選取 BizTalk Server 主控件的執行個體 (接收位置會在其上執行)。 接收處理常式必須在此主控件上執行。|  
    |**接收管線**|從下拉式清單選取接收管線，用來在此接收位置接收訊息。|  
    |**傳送管線**|從下拉式清單選取傳送管線，用來從此接收位置傳送回應。 只有和要求-回應接收埠相關聯的接收位置才能使用此清單。|  
    |**將此主要位置**|若接收埠有一個以上的接收位置，而且必須將連接埠傳遞給需要將訊息傳送至您組織的另一個實體時 (例如，商務合夥人)，若想要以此接收位置代表接收埠，請選取此核取方塊。 建立的第一個接收位置會自動選取為主要接收位置。 除非您指派其他接收位置做為主要位置，否則此屬性會繼續處於選取狀態而且無法使用。|  
  
## <a name="see-also"></a>另請參閱  
 [管理接收位置](../core/managing-receive-locations.md)