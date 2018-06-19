---
title: 如何升級協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef3f032f-28a1-4d52-9d85-d5748c9e9682
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edd9fa8e98b62ec92b1313cc1028efc5320ce17e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257886"
---
# <a name="how-to-upgrade-an-orchestration"></a>如何升級協調流程
如何更新協調流程處理長時間執行的交易或正在等候請求-回應連接埠的回應時，會將實際執行環境中執行的協調流程。

## <a name="overview"></a>概觀
 當協調流程不會處理長時間執行的交易時，您可以加以更新中所述[檢查清單： 更新 BizTalk 應用程式中的成品](../core/checklist-update-the-artifacts-in-a-biztalk-application.md)。 不過，如果協調流程有處理長時間執行的交易，就無法立即切換到協調流程的更新版本。 您必須讓原始的版本完成訊息的處理，以避免訊息遺失。 若要完成這項作業，您要將更新的協調流程部署到與原始版本相同的應用程式中。 然後再停止原始的版本，並啟動更新版本使它可以接收所有新的訊息，而舊版本則持續處理任何已傳遞的訊息。 在原始的協調流程完成所有其訊息的處理之後，請將它從部署所在的 BizTalk 應用程式中解除部署。  
  
 如需有關此案例的詳細資訊，請參閱[案例： 更新應用程式成品](../core/scenario-updating-application-artifacts.md)。  
  
> [!IMPORTANT]
>  如果有一個以上的協調流程繫結到相同的接收埠，而每個協調流程都已啟動或登錄，則您會在系統中導入重複的訊息。  
  
> [!NOTE]
>  在升級到新的協調流程時，有些協調流程執行個體會在高壓力情況下而變成「已擱置 (可繼續)」，這是因為舊的協調流程與新的協調流程在升級過程中出現競爭而造成的。 若要手動繼續這些協調流程執行個體，請參閱[如何繼續已擱置協調流程執行個體](../core/how-to-resume-suspended-orchestration-instances.md)。

## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。 您的帳戶也必須具有本機檔案系統和全域組件快取的讀取/寫入權限。 本機電腦上的「系統管理員」帳戶具有這項權限。  

如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，和[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。 
 
## <a name="update-an-orchestration"></a>更新協調流程  
  
1.  對協調流程進行必要的變更。  
  
2.  依下列方式遞增組件的版本號碼：  
  
    1.  在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案，然後**屬性**啟動專案的專案設計工具。  
  
    2.  按一下**應用程式**如果還沒有使用中] 索引標籤，然後按一下 [**組件資訊**。  
  
    3.  在右方窗格中增加組件的版本號碼。 您只應該增加主要或次要的版本號碼。 主要版本號碼是序列中的第一個數字 (**0**.0.0.0); 的次要版本號碼是序列中的第二位數 (0。**0**.0.0)。 BizTalk Server 將無法辨識版本號碼變更為序列，例如 0.0 後面。**0**.0 或 0.0.0。**0**。  
  
    4.  按一下**確定**關閉**組件資訊** 對話方塊。  
  
    5.  儲存專案。  
  
3.  從 Visual Studio 將組件部署到 BizTalk 應用程式。 如需指示，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。 請確定您選取的部署選項會將組件部署在 GAC 中。  
  
4.  測試包含協調流程的組件。  
  
5.  匯出至.msi 檔案，您的測試環境中的應用程式的組件中所述[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
    > [!NOTE]
    >  您可以使用下列步驟，對組件進行測試並將其部署到實際執行環境中。 如需開發、 測試、 預備及生產環境中的應用程式部署工作的詳細資訊，請參閱[應用程式部署工作](../core/application-deployment-tasks.md)。  
  
6.  將.msi 檔案匯入實際執行環境，其中包含您想要更新中所述的協調流程的 BizTalk 應用程式[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  
  
7.  將更新與原始協調流程中，使用相同的繫結的協調流程的繫結中所述[如何設定協調流程繫結](../core/how-to-configure-bindings-for-an-orchestration.md)。  
  
8.  取消登錄原始的協調流程，然後啟動更新的協調流程。 避免任何訊息遺失，您應該執行下列作業以程式設計方式中所述[部署和啟動新版本的協調流程以程式設計方式](../core/deploying-and-starting-a-new-version-of-an-orchestration-programmatically.md)。 或者，您可以執行下列步驟手動中所述[如何取消登錄協調流程](../core/how-to-unenlist-an-orchestration.md)，[如何登錄協調流程](../core/how-to-enlist-an-orchestration.md)，和[如何啟動協調流程](../core/how-to-start-an-orchestration.md).  
  
9. 監視系統中所述，使用 群組中樞的原始協調流程版本的執行個體頁面查詢檢視[如何檢視協調流程的執行個體資訊](../core/how-to-view-instance-information-for-an-orchestration.md)。  
  
10. 所有其作用中、 凍結和擱置的執行個體完成時，解除部署應用程式，從原始的協調流程中所述[如何從應用程式移除協調流程](../core/how-to-remove-an-orchestration-from-an-application.md)。  
  
11. 選擇性地從解除安裝的原始組件版本上執行應用程式，每一部電腦的 GAC 中所述[如何從 GAC 解除安裝組件](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4)。  
  
## <a name="see-also"></a>另請參閱  
 [更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)   
 [管理協調流程](../core/managing-orchestrations.md)