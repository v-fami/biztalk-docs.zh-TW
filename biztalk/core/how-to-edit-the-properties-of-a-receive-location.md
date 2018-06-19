---
title: 如何編輯屬性的接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [receive locations], properties
- managing [receive locations], editing
- receive locations, properties
- receive locations, editing
- editing, receive locations
- editing, properties
ms.assetid: 2b622050-a875-4896-bed6-65ca39a26dd3
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 578c5e2970e587180a7928563ebdd942c62dc396
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254462"
---
# <a name="how-to-edit-the-properties-of-a-receive-location"></a>如何編輯接收位置的屬性
本主題描述如何使用 [BizTalk Server 管理主控台] 編輯現有接收位置的屬性。 如需建立接收位置的指示，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-edit-the-properties-of-a-receive-location"></a>編輯接收位置的屬性  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 BizTalk 群組和 BizTalk 應用程式，您要編輯的接收位置屬性，然後按一下**接收位置**。  
  
3.  在右窗格中，以滑鼠右鍵按一下接收位置，然後**屬性**。  
  
4.  在**接收位置屬性**視窗中，編輯一或多個下列的屬性，然後按一下**確定**:  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|輸入接收位置的名稱。|  
    |**型別**|從下拉式清單選取傳輸類型或傳輸通訊協定。 若您變更傳輸類型，則必須設定如下所描述的傳輸屬性。|  
    |**設定**|選取傳輸類型之後，請按一下**設定**顯示**傳輸屬性**對話方塊設定配接器接收位置屬性。 如需指示，請按一下**協助**在對話方塊中。 如需設定配接器，每種類型的詳細資訊，請參閱底下的適當主題[使用配接器](../core/using-adapters.md)。|  
    |**接收處理常式**|從下拉式清單選取 BizTalk Server 主控件的執行個體 (接收位置會在其上執行)。 接收處理常式必須在此主控件上執行。|  
    |**接收管線**|從下拉式清單選取接收管線，用來在此接收位置接收訊息。|  
    |**傳送管線**|從下拉式清單選取傳送管線，用來從此接收位置傳送回應。 只有和要求-回應接收埠相關聯的接收位置才能使用此清單。|  
    |**將此主要位置**|若接收埠有一個以上的接收位置，而且必須將連接埠傳遞給需要將訊息傳送至您組織的另一個實體時 (例如，商務合夥人)，若想要以此接收位置代表接收埠，請選取此核取方塊。 建立的第一個接收位置會自動選取為主要接收位置。 除非您指派其他接收位置做為主要位置，否則此屬性會繼續處於選取狀態而且無法使用。|  
  
> [!NOTE]
>  如果您變更或修改接收位置，請重新啟動與所修改接收位置對應的外掛式主控件工作者處理序。  
  
## <a name="see-also"></a>另請參閱  
 [管理接收位置](../core/managing-receive-locations.md)