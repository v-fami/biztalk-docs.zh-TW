---
title: "如何將參考加入另一個應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: applications, referencing
ms.assetid: 6a177560-ee1f-403a-a68a-ade409a39a35
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25668e7cfcb7d810d999c01eef28e5116b46c298
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-reference-to-another-application"></a>如何新增另一個應用程式的參考
本主題說明如何使用 BizTalk Server 管理主控台，在應用程式中加入另一個應用程式的參考。 您也可以加入其他應用程式的參考，當您匯入您的應用程式使用匯入精靈中所述[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  
  
 當您想在目前應用程式中使用相同 BizTalk 群組內另一個應用程式的現有成品，便可以加入參考。 這是因為大多數類型的成品在 BizTalk 群組中必須是唯一的。 因此，您應加入另一個已包含成品之應用程式的參考，而不要在目前的應用程式中加入重複成品。 如需詳細資訊，請參閱[成品，必須是唯一的應用程式或群組](../core/artifacts-that-must-be-unique-in-an-application-or-group.md)。  
  
 當您想要使用另一個應用程式中現有的虛擬目錄或憑證時，不一定要加入參考。 而且建議您不要加入參考，因為這會造成循環參考。  
  
 匯入具有相依性的應用程式時，也會匯入參考。 新增對另一個應用程式的參考時，請記住這會影響您部署這些應用程式的方式。 如需詳細資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-add-a-reference-to-another-application"></a>若要新增另一個應用程式的參考  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下您要建立參考的應用程式。 這是您想要在其中使用另一個應用程式中所包含成品的應用程式。  
  
3.  指向**新增**，然後按一下 **參考**。  
  
4.  在**應用程式**，選取您要加入的參考 （包含的應用程式的成品或您想要使用的成品），應用程式，然後按一下核取方塊**確定**。  
  
     參考隨即加入至目前應用程式中。 在主控台樹狀結構中，目前應用程式中所參考的另一個應用程式會加上手形圖示，表示有一或多個應用程式參考它。  
  
     ![共用應用程式圖示](../core/media/sharedapplicationicon.gif "SharedApplicationIcon")  
  
## <a name="see-also"></a>另請參閱  
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)