---
title: 更新應用程式的最佳做法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 072eaf25-a1ee-4af3-b034-525a04260ef4
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75dbde61369cdc8658dd9b39fa75fe2655225222
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001727"
---
# <a name="best-practices-for-updating-applications"></a>更新應用程式的最佳作法
本主題說明您應該考慮使用更新 BizTalk 應用程式和成品時的最佳作法。  
  
## <a name="versioning"></a>版本控制  
 **實作版本控制策略**  
  
- 良好的版本控制策略是不可或缺長時間執行交易使用或無法卸下 BizTalk 應用程式進行升級或 bug 修正。 您應該計劃的所有的 BizTalk 成品的版本控制策略： 結構描述、 對應、 自訂配接器、 管線、 管線元件、 協調流程、 商務規則、 BAM 和自訂類別中的協調流程和對應的呼叫。  
  
  **符合 BizTalk 管理資料庫和全域組件快取 (GAC) 中的組件**  
  
- 請確定相同版本的組件位於 GAC 中，BizTalk 管理資料庫，讓您的應用程式已正確運作。 如果您沒有總是在部署組件時將其安裝到 GAC 中，就可能會在 GAC 和 BizTalk 管理資料庫中擁有不同的版本，這樣將會造成執行階段期間的處理錯誤。  
  
  **使用 BizTalk 組件檢查 和 遠端 GAC 工具來確認 版本控制**  
  
- **BizTalk 組件檢查] 和 [遠端 GAC 工具**(BTSAssemblyChecker.exe) 會檢查組件部署到 BizTalk 管理資料庫的版本，並確認他們正確登錄所有的 BizTalk 的 GAC 中伺服器的電腦。 若要確認所有包含的某些 BizTalk 應用程式成品的組件會安裝 BizTalk 的所有節點上，您可以使用這項工具。 此工具是搭配 solid 的版本控制策略，以確認特別並排顯示部署方法使用時，為每個 BizTalk 在電腦上，安裝正確版本的組件的一組特別有用。  
  
- 此工具是適用於 Support\Tools\x86\BTSAssemblyChecker.exe BizTalk Server 安裝媒體。  
  
  **使用版本控制產品**  
  
- 您應該使用版本控制產品，例如 Microsoft Visual Studio® Team Foundation Server 2010，追蹤和版本設定的 BizTalk 成品。 如需 Microsoft Visual Studio® Team Foundation Server 2010 的詳細資訊，請參閱[Microsoft Visual Studio® Team Foundation Server 2010](http://go.microsoft.com/fwlink/?LinkId=210637) (http://go.microsoft.com/fwlink/?LinkId=210637)  
  
  **因素成品至多個 BizTalk 應用程式**  
  
- 若要執行的 BizTalk 成品的組件版本控制，您的 BizTalk 方案組件需要考量 （封裝），以允許 BizTalk Server 版本控制的方式。 如需隔離的詳細資訊，請參閱[新增至應用程式的成品](../technical-guides/adding-artifacts-to-an-application.md)。  
  
## <a name="updating-an-application"></a>更新應用程式  
 **使用更新的應用程式的.msi 檔案**  
  
-   升級應用程式通常是在生產環境中的審慎且精確的作業。 當您升級應用程式時，您通常應該使用手動檢查清單。 不過，您可以使用.msi 檔來簡化特定步驟。 當您使用.msi 檔案時，您可以總結您的應用程式成品，到可轉散發套件。 當您向多個執行階段方塊推出更新的 Dll，或執行群組層級部署的.msi 檔案會特別有用的。 當您建立的.msi 檔案時，您應從封裝來排除所有其他不變的資源和繫結。  
  
-   如果您更新 BizTalk 組件時，您應該停止、 取消登錄、 重新登記，然後再啟動 BizTalk 成品手動之前和之後您匯入並安裝.msi 檔案。 如需有關如何更新 BizTalk 組件的詳細資訊，請參閱[檢查清單： 更新組件](../technical-guides/checklist-updating-an-assembly.md)。  
  
-   如果您升級使用並排顯示版本設定的 BizTalk Server 組件時，您必須執行手動步驟之前和之後使用.msi 檔案。 如需有關執行所需的手動步驟的詳細資訊，請參閱[檢查清單： 更新應用程式使用的並存版本控制](../technical-guides/checklist-updating-an-application-using-side-by-side-versioning.md)。  
  
## <a name="updating-an-assembly"></a>更新組件  
 **在生產環境中的組件版本遞增**  
  
- 如果您正在更新執行於實際執行環境的組件，您應該隨時遞增組件版本號碼。  
  
  **更新已更新的組件與 GAC**  
  
- 當您更新組件包含協調流程、 結構描述或對應時，您必須更新以包含新版本的組件的 GAC。 否則，BizTalk Server 會使用過期的版本。 若要這樣做，每一部執行的應用程式繫結從 GAC，解除安裝舊版包含更新的成品的組件，請確定已安裝新版本的主機執行個體。  
  
  **重新啟動之後更新組件的主控件執行個體**  
  
- 如果更新現有的應用程式中的 BizTalk 組件時，您可能需要重新啟動主控件執行個體，變更才會生效。 重新啟動主控件執行個體，就會停止所有其他主控件執行個體執行的應用程式。  
  
## <a name="updating-an-artifact"></a>更新成品  
 **解除部署相依的成品的成品，這取決於之前**  
  
- 如果您要解除部署其他成品所相依的成品，您必須先解除部署相依的成品。  
  
  > [!NOTE]  
  >  如果您執行第一次不解除部署相依的成品，BizTalk Server 管理主控台會顯示警告，並避免您不正確的順序解除部署成品。  
  
  **無法停止另一個應用程式所依賴的成品**  
  
- 如果您停止一個應用程式中另一個應用程式所相依的成品 (這可能是停止整個應用程式所產生的結果)，則相依的應用程式將無法正確運作。 如需有關如何停止應用程式的詳細資訊，請參閱 <<c0> [ 如何啟動和停止 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154729)(http://go.microsoft.com/fwlink/?LinkID=154729)。  
  
  **加入之前先移動成品的組件的參考**  
  
- 當您將成品移到新的應用程式時，除非新的應用程式有參考移動之成品所相依之成品的所在應用程式，否則也會移動該成品所相依的其他任何成品。 此外，相依於移動之成品的任何成品也會移動，除非包含這些成品的應用程式有參考新的應用程式。 當您移動成品時，系統會為您顯示也將一併移動之其他成品的清單。  
  
## <a name="updating-bindings"></a>更新繫結  
 **自動重新設定的繫結**  
  
-   當您在應用程式中更新組件時，其繫結通常都會遭到覆寫，或是組件可能根本不會繫結，進而使您必須手動重新設定繫結。 您可以使用繫結檔案來自動化此程序。 如果您要更新的組件相同的版本，可以先將繫結檔案匯出的組件，然後更新組件，則組件匯入應用程式，然後重新套用先前的繫結，透過匯入繫結檔案。 如果您要更新組件的較新版本，您可以將繫結檔案匯出、 編輯檔案以反映新的組件版本、 新的組件匯入應用程式，並匯入繫結檔案，以套用新的繫結。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 如何繫結檔案匯出的繫結](../technical-guides/how-to-export-bindings-to-a-binding-file.md)。 如需有關編輯繫結檔案的詳細資訊，請參閱 <<c0> [ 自訂繫結檔案](http://go.microsoft.com/fwlink/?LinkID=155000)(http://go.microsoft.com/fwlink/?LinkID=155000)。  
  
## <a name="starting-or-stopping-an-application"></a>啟動或停止應用程式  
 **停止應用程式更新成品**  
  
-   如果您不要停止應用程式來更新應用程式中的成品，您需要暫時停止到 MessageBox 資料庫的發行集，藉由停用端點，並停止和取消登錄任何執行中執行個體。 若要停止並取消登錄正在執行的執行個體，所有已凍結或已暫停的執行個體必須以手動方式繼續和完成，或終止。  
  
-   雖然不必為了更新成品或安裝應用程式而停止應用程式，我們還是建議您一律在更新成品時停止應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [如何將繫結匯出至繫結檔案](../technical-guides/how-to-export-bindings-to-a-binding-file.md)