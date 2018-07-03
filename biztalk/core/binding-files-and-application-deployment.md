---
title: 繫結檔案和應用程式部署 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings
- deploying [applications], binding files
- assemblies, binding files
- bindings, applying
- groups, assemblies
- applications, binding files
- binding files, applications
- bindings, hosts
- deploying, assemblies
- updating, assemblies
- assemblies, updating
- hosts, bindings
- binding files, assemblies
- applications, moving
- assemblies, deploying
- binding files, about binding files
- bindings, about bindings
- groups, deploying
- binding files, deploying
- bindings, binding files
ms.assetid: 396ad021-8001-4ed8-8b28-85b72f981fae
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 316ce46898bca23461c042f88fddb95b0d6a2f80
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004959"
---
# <a name="binding-files-and-application-deployment"></a>繫結檔案和應用程式部署
本主題提供使用繫結檔案讓 BizTalk 組件和應用程式部署更為容易的概觀資訊。 您可能會在下列案例中發現，使用繫結檔案即可避免手動設定繫結，因此可以使部署加速：  
  
-   將應用程式從一個部署環境移動到另一個部署環境。  
  
-   更新組件。  
  
-   將組件部署至多個 BizTalk 群組。  
  
## <a name="what-is-a-binding"></a>何謂繫結？  
 繫結會在邏輯端點 (例如協調流程連接埠或角色連結) 與實體端點 (例如傳送和接收埠或合作對象) 之間建立對應。 這讓通訊能在不同的 BizTalk 商務方案元件之間進行。 您可以使用 [BizTalk Server 管理主控台] 建立繫結。  
  
## <a name="what-is-a-binding-file"></a>何謂繫結檔案？  
 繫結檔案是一種 .xml 檔案，其中包含在 BizTalk 組件、應用程式或群組之範圍中的每個 BizTalk 協調流程、管線、對應或結構描述的繫結資訊。 繫結檔案描述每個協調流程所繫結的主控件、其信任層級，以及每個傳送埠、傳送埠群組、接收埠、接收位置和已設定合作對象的設定。 您可以產生繫結檔案，然後將其所包含的繫結套用至組件、應用程式或群組，以避免需要在不同的部署環境中手動設定繫結。  
  
## <a name="why-use-binding-files"></a>為何使用繫結檔案？  
 您可能需要在下列案例中使用繫結檔案。  
  
### <a name="moving-from-one-environment-to-another"></a>從一個環境移至另一個環境  
 您可以使用繫結檔案，讓應用程式能夠更容易地從一個部署環境移至另一個部署環境，例如從開發環境移至測試環境。 這是因為繫結通常都必須為不同的部署環境重新設定，不過藉由使用繫結檔案，即可避免重複執行這項手動組態步驟。  
  
 您可以進行此項的一種方式，便是建立繫結庫，並在將應用程式部署到新環境時，從其中加以選取。 例如，您可以為測試環境建立繫結檔案，並為實際執行環境建立另一個繫結檔案，然後將這兩者都新增到應用程式中。 當您將應用程式匯入到測試環境時，即可選取套用測試繫結的選項。 同樣的，當您將應用程式匯入到實際執行環境時，也可以選取套用實際執行繫結的選項。 這樣即可避免為不同環境手動重新設定繫結的需要。 另一種方式則是在將應用程式匯入到目前的環境後，再匯入您所建立適用於該環境的繫結。 這樣便會自動套用繫結。  
  
### <a name="updating-an-assembly"></a>更新組件  
 當您在應用程式中更新組件時，其繫結通常都會遭到覆寫，或是組件可能根本不會繫結，進而使您必須手動重新設定繫結。 若要避免這種問題，您可以使用如下的繫結檔：  
  
-   **正在更新相同版本的組件。** 如果組件具有早期繫結連接埠或動態連接埠，而且您有在 [ BizTalk Server 管理主控台] 中變更連接埠組態，當您以具有相同版本號碼的組件來更新組件時，便會遺失設定。 您可以為將要更新的組件匯出繫結檔。 在更新組件後，您可以將組件匯入到應用程式中，然後再匯入其繫結檔以重新套用先前的繫結。  
  
-   **更新組件的較新版本。** 您可以為將要更新的組件匯出繫結檔，然後予以編輯以反映新的組件版本。 在將新的組件版本匯入到應用程式後，您便可以將繫結檔匯入到應用程式以套用繫結。 如需編輯繫結檔案的指示，請參閱 <<c0> [ 自訂繫結檔案](../core/customizing-binding-files.md)。  
  
### <a name="deploying-an-assembly-to-multiple-biztalk-groups"></a>將組件部署至多個 BizTalk 群組  
 當您將組件部署至多個 BizTalk 群組時，可以一起傳輸組件的繫結和組件本身。 這樣即可避免為每個群組中的組件分別設定繫結。 您可以用下列方法進行：  
  
1.  匯出組件的繫結，進而為您所要部署的組件建立繫結檔。  
  
2.  將組件及其繫結檔新增至應用程式。 如果您在部署組件時要與其他成品分開，應用程式便只能包含組件和繫結檔。  
  
3.  匯出應用程式的 .msi 檔案，並確定選取要匯出的繫結檔。  
  
4.  將應用程式 .msi 檔案匯入到您要在其中部署的 BizTalk 群組和應用程式中。 在匯入時，檔案中的繫結便會自動套用至組件。  
  
## <a name="how-can-i-generate-and-use-binding-files"></a>我如何能夠產生和使用繫結檔？  
 BizTalk 組件、 應用程式或群組，不會自動產生繫結檔案，但您可以產生繫結檔案匯出繫結中所述[匯出的繫結](../core/exporting-bindings6.md)。 您可以再匯入繫結檔案的應用程式或群組，如中所述[如何匯入至 BizTalk 應用程式的繫結](../core/how-to-import-bindings-into-a-biztalk-application.md)並[如何匯入到 BizTalk 群組的繫結](../core/how-to-import-bindings-into-a-biztalk-group.md)，它會自動套用其繫結。  
  
 或者，您可以新增繫結檔案至應用程式以便中所述，將會匯入另一個群組，而不是立即套用的應用程式時，會套用其繫結[如何將繫結檔案新增至應用程式](../core/how-to-add-a-binding-file-to-an-application2.md). 只要使用最後一種方法，您就能將多個繫結檔新增到應用程式，並能選擇性地指定每個繫結檔的目標部署環境。 當您匯入應用程式時，然後您可以選取要套用，哪些繫結中所述，根據目標部署環境中，[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 使用最後一種方法，您也可以針對應用程式中的不同組件而匯入個別的繫結檔。  
  
 在產生繫結檔後，您依然能夠加以編輯以變更其繫結資訊。 如需詳細資訊，請參閱 <<c0> [ 自訂繫結檔案](../core/customizing-binding-files.md)。  
  
## <a name="how-are-bindings-applied"></a>繫結是如何套用的？  
 當繫結檔匯入至應用程式，或是當應用程式匯入至新的 BizTalk 群組時，便會套用繫結。 在使用繫結檔時，最好先瞭解成品如何繫結到主控件，以及套用繫結的順序。  
  
### <a name="binding-to-hosts"></a>繫結到主控件  
 當繫結個別匯出或是做為應用程式的一部分而匯出時，主控件和信任層級便會存放在繫結檔中，如下所示：  
  
- **傳送埠。** 與傳送處理常式相關聯之主控件的信任層級。  
  
- **接收位置。** 與接收處理常式相關聯之主控件的信任層級。  
  
- **協調流程。** 主控件的信任層級。  
  
  當繫結匯入至應用程式，或是應用程式從 .msi 檔案匯入至新的 BizTalk 群組時，繫結檔中的主控件和信任層級便會與應用程式中的主控件和信任層級相符，如下所示：  
  
- **傳送埠。** 傳送埠會繫結至具有相同名稱的傳送處理常式，並會繫結至與存放在繫結檔中的主控件具有相同信任層級的主控件。  
  
- **接收位置。** 接收位置會繫結至具有相同名稱的接收處理常式，並會繫結至與存放在繫結檔中的主控件具有相同信任層級的主控件。  
  
- **協調流程。** 協調流程會繫結至具有相同名稱的主控件，以及在繫結檔中具有相同信任層級的主控件。  
  
### <a name="order-in-which-bindings-are-applied"></a>套用繫結的順序  
 當您匯入應用程式時，將依下列順序套用繫結：  
  
1. 並非透過繫結檔案明確加入至應用程式，而是使用者明確選定欲匯出至應用程式 .msi 檔案的應用程式繫結 (由 BizTalk Server 所產生)。  
  
2. 已經加入應用程式的繫結檔中，而且沒有指定目標部署環境的繫結。 這些繫結不會以特定的順序套用。  
  
3. 已經加入應用程式的繫結檔，而且其相關聯目標部署環境與應用程式匯入所選定的部署環境相符的繫結。 這些繫結不會以特定的順序套用。  
  
   由於繫結是在匯入過程中套用，新的繫結會覆寫先前已套用的同名繫結。 也就是說，同名的繫結當中最後套用的繫結將會生效。  
  
   例如，如果現有的應用程式包括名為 SendPort1 的傳送埠，而且套用的繫結檔以相同名稱描述某個傳送埠，繫結檔中的設定便會覆寫 SendPort1 的現有設定。 例如，如果現有的應用程式包括名為 ErrorHandling.ErrorHandler.ResubmitLogic 的協調流程，而且繫結檔描述具有相同名稱的協調流程，該協調流程的所有現有繫結便會以繫結檔中的繫結寫入。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)