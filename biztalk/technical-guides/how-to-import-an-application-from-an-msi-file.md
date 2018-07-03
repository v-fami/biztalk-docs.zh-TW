---
title: 如何從.msi 檔案匯入應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5472df9-9f1e-42d5-82e0-cc559caf56b3
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e1cea55ba50a094258a3fcf07eedf30466566d3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004919"
---
# <a name="how-to-import-an-application-from-an-msi-file"></a>如何從.msi 檔案匯入應用程式
您可以使用 BizTalk Server 管理主控台或 BTSTask 匯入 MSI 精靈 從.msi 檔案匯入 BizTalk 應用程式，到目標環境中的 BizTalk 群組，並在群組中的個別主控件執行個體上安裝應用程式。 完整匯入程序會執行下列作業：  
  
- 群組層級部署的應用程式  
  
- 安裝應用程式的伺服器層級。  
  
  **群組層級的應用程式部署**  
  
  藉由執行匯入 MIS 精靈，從 BizTalk Server 管理主控台或 BTSTask 的執行，您可以執行在群組中的伺服器上的應用程式群組層級部署。 群組層級部署會執行下列動作：  
  
- 為群組中建立應用程式和其成品  
  
- 匯入.msi 套件中的繫結  
  
- 將所有 BizTalk Server 組件及其成品都部署到 BizTalk 管理資料庫群組  
  
- 執行指令碼指定在匯入時執行。  
  
  如果您在應用程式中新增環境特定繫結檔案，您必須選取您想要在匯入時套用的繫結。  
  
  **伺服器層級應用程式安裝**  
  
  您可以在群組中的每部伺服器上執行應用程式的伺服器層級安裝藉由按兩下.msi 檔案本身，或執行安裝程序，在匯入 MSI 精靈結尾處。 而不是在每個群組執行一次，它通常是每個 BizTalk server 群組的成員。 伺服器層級安裝會執行下列動作：  
  
- 所有的 BizTalk Server 組件和相依性組件安裝到全域組件快取的伺服器，使這台電腦具有所有所需的執行階段二進位檔  
  
- 可能是方案的一部分，例如，協調流程發佈為 Web 服務的相關 Web 服務推出。  
  
- 適用於電腦特定的變更，例如預先建立 MSMQ 佇列，或建立檔案放置資料夾結構和權限，可以使用指令碼的協助。  
  
  當您執行.msi 檔案安裝應用程式時，.msi 檔案中新增或移除程式 清單中，建立登錄項目，並加速自動化部署的成品和正確的順序及其相依性的部署。  
  
  如需有關如何安裝 BizTalk 應用程式的詳細資訊，請參閱 <<c0> [ 如何安裝應用程式](../technical-guides/how-to-install-an-application.md)。  
  
  **完整的應用程式部署和安裝程序**  
  
  匯入 MSI 精靈會部署群組上的應用程式。 它不會在群組中的個別伺服器上安裝應用程式。 如果應用程式包含以檔案為基礎的成品，您需要在每個在應用程式 （和任何執行相依於此應用程式的應用程式的電腦） 中執行的組件的主控件執行個體上安裝應用程式。 您可以執行以便在伺服器上您匯入 MSI 精靈 上執行，不過，方法是選取**執行應用程式安裝精靈在本機電腦上安裝應用程式**在匯入成功 頁面上所顯示的核取方塊匯入 MSI 精靈。 則可以在群組中的其他伺服器上按兩下.msi 檔案，在每一部伺服器上。  
  
  如果您已準備好測試應用程式，可以匯入 BizTalk 群組中的測試環境。 如果您的應用程式是供預備或生產環境，可以匯入其中一個環境。  
  
## <a name="important-considerations"></a>重要考量因素  
 當匯入 BizTalk 應用程式，從.msi 檔案，請注意下列：  
  
- **您必須指定您想要覆寫標準的匯入程序中的成品。** 如果您想要覆寫現有成品，請選取 匯入.msi 檔案時覆寫現有成品的選項。  
  
- **匯入繫結會覆寫現有的繫結。** 在現有應用程式中匯入包含繫結的 .msi 檔案時，現有繫結會遭到具有相同名稱的匯入繫結所覆寫。 即使您沒有在匯入 .msi 檔案時選取覆寫現有成品選項也會如此。 如果不想用匯入的應用程式繫結來覆寫要匯入 .msi 檔案的應用程式的現有繫結，則應該在匯出作業期間選擇不要將繫結檔案做為匯出資源。 如需有關設定匯出資源的詳細資訊，請參閱[如何匯出 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154848)(http://go.microsoft.com/fwlink/?LinkID=154848)。  
  
  由於繫結是在匯入過程中套用，新的繫結會覆寫先前已套用的同名繫結。 也就是說，同名的繫結當中最後套用的繫結將會生效。 當您匯入應用程式時，將依下列順序套用繫結：  
  
1.  並非透過繫結檔案明確加入至應用程式，而是使用者明確選定欲匯出至應用程式 .msi 檔案的應用程式繫結 (由 BizTalk Server 所產生)。  
  
2.  已明確加入，但未指定目標部署環境的繫結檔案。 套用此集合中的繫結時，並無特定順序。  
  
3.  已明確加入，且其相關聯目標部署環境與應用程式匯入所選定的部署環境相符的繫結。 套用此集合中的繫結時，並無特定順序。  
  
- **指定的主控件必須存在。** 若要應用程式從.msi 檔案匯入，對應至主應用程式.msi 檔案中包含的應用程式繫結中指定的主機必須已存在於 BizTalk 群組，或匯入作業將會失敗。 此外，主控件的信任層級也必須相符合。  
  
- **相依性可能會造成顯著的影響，匯入作業時。** 當您匯入的應用程式，會相依於另一個應用程式時，適用下列規則：  
  
  -   如果您要匯入的應用程式相依於另一個應用程式中的成品，您必須從第一個應用程式，第二個應用程式中加入的參考。 應用程式和必要的成品必須已存在於目的地群組中。 匯入精靈 可讓您加入參考。 不過，如果您使用 BTSTask 的 ImportApp 命令，您必須加入之後匯入的應用程式的參考。 如需詳細資訊，請參閱 <<c0> [ 如何加入另一個應用程式的參考](http://go.microsoft.com/fwlink/?LinkId=155011)(http://go.microsoft.com/fwlink/?LinkId=155011)。 匯入精靈會比對群組中現有應用程式的參考，並讓您選擇要新增參考或變更現有的參考。 雖然 BizTalk Server 會驗證參考的應用程式是否存在，但我們還是建議您採取另一個步驟，也就是驗證所參考的應用程式是否包含必要的成品。  
  
  -   當您安裝應用程式時，也必須安裝它所相依的任何應用程式。 當您安裝與某個成品有相依性的應用程式 (例如包含在另一個應用程式中的 BizTalk 組件) 時，您必須先安裝包含該成品的應用程式。 例如，如果您想要安裝應用程式 A，而它相依於應用程式 B 中的組件，則您必須先安裝應用程式 B。 接著，您也可以安裝應用程式 a。如需有關如何安裝 BizTalk 應用程式的詳細資訊，請參閱 <<c0> [ 如何安裝應用程式](../technical-guides/how-to-install-an-application.md)。  
  
  -   如果您想要將應用程式匯入到不同的 BizTalk 群組，並於該群組中執行它，您也必須匯入此應用程式所相依的任何成品。 第一次匯入的應用程式包含參考的成品，或藉由將需要它的應用程式所需的成品，您可以這麼做。 如需有關如何匯入 BizTalk 應用程式的詳細資訊，請參閱 <<c0> [ 如何從.msi 檔案匯入應用程式](../technical-guides/how-to-import-an-application-from-an-msi-file.md)。  
  
  如需詳細考量和從.msi 檔案匯入 BizTalk 應用程式的相關資訊，請參閱[如何匯入 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154827)(http://go.microsoft.com/fwlink/?LinkID=154827)。  
  
## <a name="how-to-import-an-application"></a>如何匯入應用程式  
 如需從.msi 檔案匯入 BizTalk 應用程式的指示，請參閱 <<c0> [ 如何匯入 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154827)(http://go.microsoft.com/fwlink/?LinkID=154827)。