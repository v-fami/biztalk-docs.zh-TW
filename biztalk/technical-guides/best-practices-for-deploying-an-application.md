---
title: "部署應用程式的最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53852303-d368-4f9e-b4e2-f5918f65000b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25d24eda11d9547b545445239e783ac3bfee4057
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-deploying-an-application"></a>部署應用程式的最佳作法
本主題列出您在部署 BizTalk 應用程式應該遵循的最佳作法。  
  
## <a name="deploying-a-biztalk-application"></a>部署 BizTalk 應用程式  
 **文件應用程式部署程序**  
  
-   請確定應用程式部署中使用的程序記載於深度，因此您需要的部署方式執行，並且知道如何進一步部署或解除部署記錄。 無法編寫指令碼的任何項目應該記錄詳細的步驟。 這應該包含記錄到外部系統和協力廠商元件部署的任何變更。  
  
 **指令碼應用程式部署**  
  
-   最多的應用程式部署步驟指令碼越好。 指令碼部署程序期間減少人為錯誤的風險。  
  
## <a name="creating-a-biztalk-application"></a>建立 BizTalk 應用程式  
 **指令碼建立的 BizTalk 應用程式與.msi 檔案**  
  
-   BtsTask.exe 可用來建立 BizTalk 應用程式的指令碼。 如果應用程式的建立已編寫指令碼，然後封裝能夠自動建置組建伺服器上使用自動化程序。 如需指令碼建立的應用程式的詳細資訊，請參閱[部署和管理 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154210)(http://go.microsoft.com/fwlink/?LinkID = 154210) 和[BizTalk Server 2006： 了解 BizTalk Server 應用程式部署](http://go.microsoft.com/fwlink/?LinkID=101599)(http://go.microsoft.com/fwlink/?LinkID = 101599) 白皮書。  
  
    > [!NOTE]  
    >  技術白皮書也會套用至[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。  
  
## <a name="deploying-a-biztalk-assembly"></a>部署 BizTalk 組件  
 **永遠不會部署在實際執行電腦上的從 Visual Studio 組件**  
  
-   在開發過程中，開發人員必須經常重新部署組件從 Visual Studio。 為了重新部署，Visual Studio 可能解除部署、解除繫結、停止及取消登錄組件中包含的成品。 雖然這在開發環境中是必要且適當的動作，但卻可能在實際執行環境中造成無法預期的嚴重後果。 基於這個理由，以及防止任何人都部署在實際執行電腦上的從 Visual Studio 組件，我們建議您永遠不會實際執行電腦上安裝 Visual Studio。  
  
-   此外，也絕對不要從執行 Visual Studio 的電腦參考實際執行資料庫。  
  
## <a name="adding-artifacts-to-a-biztalk-application"></a>將成品新增至 BizTalk 應用程式  
 **群組在一起的單一應用程式的相關的成品**  
  
-   盡可能將相關的成品放置在相同的 BizTalk 應用程式中。 這可讓您將成品做為單一實體管理和部署，讓管理變的更容易。 您可將支援相同商務程序或執行類似功能的成品分組到單一應用程式。  
  
 **部署個別的應用程式共用的成品**  
  
-   如果成品將由兩個以上的應用程式共用，請將共用的成品部署到個別的應用程式。 例如，如果兩個應用程式共用某結構描述，請將該結構描述放置到個別的應用程式中。 我們建議您這樣因為只有一個成品在 BizTalk 群組中的只能有單一的本機唯一識別碼 (LUID)。 LUID 包含成品名稱以及選擇性的其他屬性。 如果您將成品包含在一個應用程式，然後建立它的參考從另一個應用程式，參考的應用程式可能無法正確運作時停止包含該成品的應用程式。  
  
     這個最佳方法適用於所有成品類型，除了檔案之外，例如讀我檔案和指令碼，它們會做為成品的檔案類型新增至應用程式。 這是因為具有相同名稱的多個檔案成品可以部署在 BizTalk 群組中。 因此，您可使用在兩個以上的應用程式中具有相同名稱的檔案。 在此情況下，停止一個應用程式時，不會影響其他應用程式。 如需有關如何新增檔案成品的詳細資訊，請參閱[如何將檔案新增至應用程式](http://go.microsoft.com/fwlink/?LinkId=154997)(http://go.microsoft.com/fwlink/?LinkId=154997)。  
  
 **部署個別的應用程式共用的網站**  
  
-   如果網站將由一個以上的商務方案共用，請將網站部署到個別的應用程式。 這是因為當您解除安裝 BizTalk 應用程式時，任何屬於該應用程式的網站虛擬目錄都會被移除，即使該網站正在執行中也一樣。 如果另一個商務方案共用該網站，則其他商務方案將無法再正常運作。  
  
 **部署共用的原則中個別的應用程式**  
  
-   如果兩個以上的應用程式使用一個原則，您應該將其部署到個別的應用程式，而不要從一個應用程式建立對另一個應用程式的參考。 這是因為當您停止應用程式時，其原則也會被解除部署。 如果您停止的應用程式中包含另一個應用程式使用的原則，該原則在兩個應用程式都將無法再運作。  
  
 **部署個別的應用程式共用的憑證**  
  
-   如果憑證由兩個以上之應用程式中的傳送埠或接收位置使用，您應該將該憑證部署到個別的應用程式中，然後從需要使用該憑證的應用程式參考此應用程式。 這是因為只有一個 BizTalk 群組中的成品可以有單一的 LUID，所以無法匯入兩個不同的應用程式中相同的憑證。 如果您嘗試匯入使用相同憑證的兩個應用程式，第一個匯入會成功，第二個匯入則會失敗。 在此情況下，使用覆寫匯入選項無法修正此問題，因為您想要覆寫的現有憑證包含在另一個應用程式中。  
  
## <a name="exporting-and-importing-a-biztalk-application"></a>匯出和匯入 BizTalk 應用程式  
 **在部署大型的.msi 檔案時，您可能需要增加 BizTalk Server 用來部署應用程式的 COM + 元件預設交易逾時**  
  
-   如果您嘗試部署的.msi 檔案非常大 (超過 100 MB)，則應用程式不會部署內的 BizTalk Server 應用程式部署期間所使用的 COM + 元件預設交易逾時。 如果交易相關聯這些 COM + 元件逾時之前完成部署，部署將會失敗。 如果您正在部署非常大的.msi 檔案，然後考慮其中一種方法，以緩和此問題：  
  
-   部署數個較小.msi 檔案，而不是一個大型的.msi 檔案。  
  
    -   增加元件服務和元件服務 管理介面中的 Microsoft.biztalk.applicationdeployment.group 元件與關聯的 3000 秒預設交易逾的時。 這些元件分別屬於 Microsoft.BizTalk.ApplicationDeployment.Engine 和 Microsoft.Biztalk.Deployment COM + 應用程式。 如需詳細資訊，請參閱 Microsoft 知識庫文章 287499，[如何變更 MTS 或 COM + 交易逾時值](http://go.microsoft.com/fwlink/?LinkId=109589)(http://go.microsoft.com/fwlink/?LinkId=109589)。  
  
 **防止遭到覆寫的繫結**  
  
-   如果不想用匯入的應用程式繫結來覆寫要匯入 .msi 檔案的應用程式的現有繫結，則應該在匯出作業期間選擇不要將繫結檔案做為匯出資源。  
  
 **確保安全的.msi 檔案**  
  
-   .msi 檔案可能包含機密資料。 請務必採取步驟，以協助確保檔案安全。 如需.msi 檔案安全性的詳細資訊，請參閱[安全性和 Windows Installer](http://go.microsoft.com/fwlink/?LinkId=154998) (http://go.microsoft.com/fwlink/?LinkId=154998)。  
  
 **確保繫結檔案的安全**  
  
-   繫結檔案可能包含機密資料。 請務必採取步驟，以協助確保檔案安全。  
  
 **沒有任何人的成品進行變更時，將匯出排程**  
  
-   當使用者不太可能會對成品進行變更的時間排程匯出作業。 這可能是很重要，因為如果使用者正在修改資料庫為基礎的成品、 虛擬目錄、 憑證或原則，匯出作業正在進行時，所做的變更將不會反映在匯出的.msi 檔案中。  
  
## <a name="importing-a-biztalk-application"></a>匯入 BizTalk 應用程式  
 **.msi 檔案匯入的指令碼**  
  
-   BtsTask.exe 可以用於指令碼的現有 BizTalk.msi 檔案匯入。 如需指令碼匯入.msi 檔案的詳細資訊，請參閱[部署和管理 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154210)(http://go.microsoft.com/fwlink/?LinkID = 154210) 和[BizTalk Server 2006： 了解 BizTalk Server 應用程式部署](http://go.microsoft.com/fwlink/?LinkID=101599)(http://go.microsoft.com/fwlink/?LinkID = 101599) 白皮書。  
  
    > [!NOTE]  
    >  技術白皮書也會套用至[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。  
  
-   您可以加入做為前置處理或後置處理指令碼執行的指令碼。 不過，您必須在您的指令碼來檢查環境變數，以判斷哪些指令碼正在執行中 （匯入、 安裝或解除安裝） 的內容中包含邏輯，並據以處理。 如需有關如何使用前置和後置處理指令碼的詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](http://go.microsoft.com/fwlink/?LinkId=154995)(http://go.microsoft.com/fwlink/?LinkId=154995)。  
  
 **確認參考的成品存在**  
  
-   當您要匯入的應用程式有另一個應用程式的參考時，BizTalk Server 會驗證參考的應用程式存在。 不過，它無法驗證您的應用程式所相依的成品會包含在參考的應用程式。 當您匯入另一個應用程式具有成品的相依性的應用程式時，我們建議您確認參考的應用程式包含成品的必要的成品。  
  
 **從.msi 檔案匯入已阻止在全域組件快取中儲存已變更的組件**  
  
-   若要更新應用程式中的成品，匯入已變更或更新成品從.msi 檔案的應用程式。 如果您未使用的成品匯入的.msi 檔案，您必須在全域組件快取中儲存已變更的組件更新群組中的所有伺服器。  
  
 **若要更新的伺服器總數子集處理群組的主機**  
  
-   在更新應用程式中的成品時，您通常必須更新 BizTalk 群組中的所有伺服器。 不過，如果您使用主機處理的群組，您只需要更新的群組中的伺服器總數子集。  
  
 **如果匯入作業逾時，應用程式分割成其他.msi 檔案**  
  
-   匯入作業會逾時，如果它超過 3600 秒的持續時間。 如果您嘗試匯入.msi 檔案，且作業逾時，您應該重新匯出應用程式，並選取要匯出的成品的子集分割到多個.msi 檔案的應用程式的內容。 如需匯出至.msi 檔案的應用程式的詳細資訊，請參閱[如何匯出 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154848)(http://go.microsoft.com/fwlink/?LinkID=154848)。