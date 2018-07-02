---
title: 如何部署與現有版本執行並排顯示的應用程式的新版本 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1677c6a5-2c4c-4d70-ab83-f7e0bb3aaf6e
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9399543219613809efb5f8a40c9d2129ba4976ad
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988855"
---
# <a name="how-to-deploy-a-new-version-of-an-application-to-run-side-by-side-with-an-existing-version"></a>如何部署應用程式的新版本，使其與現有版本並存執行。
如何部署新的版本，將執行並排顯示的應用程式與現有版本。 

## <a name="overview"></a>概觀
您可能會想要這麼做，以累加方式展開主要應用程式升級；例如，開始時先讓一部分的商務夥伴使用，而不是一下子就提供給所有的夥伴使用。 使用這種方式，可讓您繼續執行現有的應用程式來服務尚未使用新版本的使用者，直到您準備好完全轉入新版本為止。 如需此案例的背景資訊，請參閱[案例： 部署兩個版本的應用程式](../core/scenario-deploying-two-versions-of-an-application.md)。  
  
 與建立組件版本不同，您並非以遞增版本號碼的方式建立應用程式版本。 而是建立名稱不同於原始應用程式的新應用程式，再以應用程式成品的新版本填入。  
  
 因為有許多類型的成品 (例如，組件) 只能存在於 BizTalk 群組中的一個應用程式，所以您必須遞增已存在於群組內之任何組件的版本號碼，才可以將它們部署到新的應用程式中。 如需詳細資訊，請參閱 <<c0> [ 成品，必須是唯一的應用程式或群組](../core/artifacts-that-must-be-unique-in-an-application-or-group.md)。  

## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。 您的帳戶也必須擁有本機檔案系統和全域組件快取的讀取/寫入權限。 本機電腦上的「系統管理員」帳戶具有這項權限。  

如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。 
  
## <a name="deploy-a-new-version-of-an-application"></a>部署應用程式的新版本  
  
1. 在 Visual Studio 中，對您要部署到新版應用程式中的組件進行任何必要的變更  
  
2. 依下列方式遞增每個組件的版本號碼：  
  
   1.  在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案，然後**屬性**為專案啟動專案設計工具。  
  
   2.  按一下 **應用程式**索引標籤上，如果不是使用中，然後按一下**組件資訊** 按鈕。  
  
   3.  增加組件版本號碼，然後按一下 **確定**。  
  
   4.  儲存專案。  
  
   > [!NOTE]
   >  請使用「管線設計師物件模型」，避免在遞增組件版本時發生結構描述衝突。  
  
3. 在方案的每個專案的部署屬性中，執行以下動作：  
  
   - 將應用程式名稱變更為新應用程式所要使用的名稱。  
  
   - 確定已選取會將組件安裝在全域組件快取 (GAC) 中的選項。  
  
     如需相關指示，請參閱 <<c0> [ 如何在 Visual Studio 中的 設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。 當您部署方案時，組件將會部署到新的應用程式中，並且安裝在 GAC 內。  
  
4. 部署包含該組件的方案。 如需相關指示，請參閱 <<c0> [ 如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)。  
  
5. 指定您希望夥伴將訊息傳送到的新 URL，以建立新的接收埠和任何必要的接收位置。 如需相關指示，請參閱 <<c0> [ 如何建立接收埠](../core/how-to-create-a-receive-port.md)。 另請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
6. 如有必要，建立適當的傳送埠，如中所述[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。  
  
7. 繫結至新建立新的應用程式接收和傳送埠，如中所述[如何設定應用程式](../core/how-to-configure-an-application.md)。  
  
8. 中所述，從您的測試環境匯出至.msi 檔案的應用程式[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
   > [!NOTE]
   >  您可以使用下列步驟，對應用程式進行測試並將其部署到實際執行環境中。 如需開發、 測試、 預備及生產環境中的應用程式部署工作的詳細資訊，請參閱[應用程式部署工作](../core/application-deployment-tasks.md)。  
  
9. 在您的生產環境中的 BizTalk 群組應用程式.msi 檔案匯入中所述[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 如果應用程式需要參考，您可以將它們時使用 [匯入 MSI 精靈] 中，或更新版本中所述[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。  
  
10. 將執行它，每個主控件執行個體上安裝新的應用程式，如中所述[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。 確認是否已在每台裝載組件之電腦的 GAC 中安裝每個更新的組件。 如有必要，將組件安裝在 GAC 中，如中所述[如何將組件安裝在 GAC 中](../core/how-to-install-an-assembly-in-the-gac.md)。  
  
11. 執行完整啟動應用程式中所述[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。  
  
12. 通知您的夥伴開始傳送訊息至新的 URL。 他們這麼做之後，應用程式便會開始處理指定夥伴的訊息。  
  
## <a name="see-also"></a>另請參閱  
 [更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)