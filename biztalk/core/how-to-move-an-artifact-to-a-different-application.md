---
title: 如何將成品移至不同的應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- artifacts, moving
- applications, artifacts
ms.assetid: 861e7782-0566-4478-a0bd-f8ced1ea6d56
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a76da726672d122935d6c7b393b403f11bb9068
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993503"
---
# <a name="how-to-move-an-artifact-to-a-different-application"></a>如何將成品移到另一個應用程式
本主題描述如何使用 BizTalk Server 管理主控台的 [移至應用程式] 命令，在 BizTalk 群組內將成品從某個應用程式移到另一個。 如果您需要將已經存在於某個應用程式中的成品用於相同 BizTalk 群組內的另一個應用程式，可能會想要這樣做。  
  
 在移動成品時，請牢記下列要點：  
  
-   **這些應用程式必須在相同的群組。** 只有當成品移動來源的應用程式與成品移入的目標應用程式位於相同 BizTalk 群組的情況下，[移至應用程式] 命令才會執行。 如果您想要將此成品移到另一個群組中的應用程式，可以從此成品目前所在的應用程式匯出此成品，然後將它匯入到新的應用程式，或是將此成品加入到此應用程式。 如需相關指示，請參閱 <<c0> [ 如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)，[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)，並[如何建立或新增成品](../core/how-to-create-or-add-an-artifact.md)。 您必須再手動移除該成品從原始的應用程式中所述[如何從應用程式移除成品](../core/how-to-remove-an-artifact-from-an-application.md)。  
  
-   **移動成品時，可能也會移動的成品它而定，或相依於它。** 當您將成品移到新的應用程式時，除非新的應用程式有參考移動之成品所相依之成品的所在應用程式，否則也會移動該成品所相依的其他任何成品。 此外，相依於移動之成品的任何成品也會移動，除非包含這些成品的應用程式有參考新的應用程式。 當您移動成品時，系統會為您顯示也將一併移動之其他成品的清單。  
  
> [!NOTE]
>  如果您需要在兩個或多個應用程式中使用相同的成品，您可能需要建立一項參考，從您想要使用此成品的應用程式參考到目前包含此成品的應用程式。 這是因為某些類型的成品在 BizTalk 群組中必須是唯一的。 如需詳細資訊，請參閱 <<c0> [ 成品，必須是唯一的應用程式或群組](../core/artifacts-that-must-be-unique-in-an-application-or-group.md)。 如需新增參考的指示，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。 請注意，新增對另一個應用程式的參考會在應用程式之間建立相依性，也會影響您必須部署這些應用程式的方式。 如需背景資訊，請參閱 <<c0> [ 相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。  
  
## <a name="prerequisites"></a>先決條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-move-an-artifact-to-a-different-application"></a>若要將成品移到不同的應用程式  
  
1. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開 [BizTalk 群組]，然後再展開 [想要移動之成品的應用程式。  
  
3. 按一下包含您想要移動，以滑鼠右鍵按一下成品，然後按一下 [成品] 資料夾**移至應用程式**。  
  
4. 在 **接收端應用程式**方塊，按一下箭頭，然後按一下 您要移動之成品的應用程式。  
  
    **移動成品**方塊會顯示要移動，以及所有相依的成品，也會移動的成品。  
  
5. 按一下 [確定] 。  
  
## <a name="see-also"></a>另請參閱  
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)