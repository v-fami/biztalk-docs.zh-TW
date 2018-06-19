---
title: BizTalk 應用程式部署的開發工作 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- developing, deploying
- deploying [applications], developing
- applications, tasks
- deploying [applications], warnings
- applications, developing
- developing, tasks
ms.assetid: b441d4f4-122e-4caf-8381-723c6142b0b6
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 237a3f95fa33b8265be9d7af2a55ed14e2bbe408
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242550"
---
# <a name="development-tasks-for-biztalk-application-deployment"></a>BizTalk 應用程式部署的開發工作
以下是從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 將 BizTalk 組件部署到 BizTalk 應用程式、完成此應用程式，以及準備將它部署到測試環境的相關步驟。 這個部署案例在開發環境中極為常見，在此環境下，程式設計人員會開發及偵錯特定的 BizTalk 商務方案。  
  
> [!IMPORTANT]
>  絕對不要在實際執行電腦中執行本主題中說明的工作。 在開發過程中，開發人員通常必須從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 重新部署組件。 為了重新部署，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 可能會解除部署、解除繫結、停止及取消登錄存在於相同或不同應用程式中的組件。 雖然這在開發環境中是必要且適當的動作，但卻可能在實際執行環境中造成無法預期的嚴重後果。 此外，為了避免任何人嘗試在實際執行電腦上從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 部署組件的可能性，我們建議您不要在實際執行電腦上安裝 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
1.  **開發和建置 BizTalk 組件。** 您開始建立 BizTalk 商務方案中的[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，使用協調流程、 結構描述、 對應和管線。 在處理此方案時，您會將它建置到一或多個 BizTalk 組件中。 如需詳細資訊，請參閱[開發 BizTalk Server 應用程式](../core/developing-biztalk-server-applications.md)。 您也可以開發及建置讓您的方案運作所需的任何非 BizTalk .NET 組件。  
  
2.  **設定部署屬性。** 當您準備好要部署 BizTalk 組件時，您設定部署屬性在每個[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案中的專案。 除了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 屬性 ([伺服器]、[組態]、[資料庫]、[重新部署]、[重新啟動主控件執行個體] 和 [安裝到全域組件快取]) 之外，您也可以設定 [應用程式名稱] 屬性。 這個屬性會指定您要將每一個組件部署到哪一個 BizTalk 應用程式中。 如果 [應用程式名稱] 是空的，該組件就會部署到預設的應用程式。 如需詳細資訊，請參閱[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。 若要部署非 BizTalk .NET 組件，您必須將這些組件加入到 BizTalk 應用程式。 這是一個單獨的步驟，將於之後的步驟 4 說明。  
  
3.  **將 BizTalk 組件部署到本機電腦上執行的 BizTalk Server。** 您可以部署 BizTalk 組件，從功能表選項，以滑鼠右鍵按一下[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案，然後選取 [部署] 命令。 這樣會在方案中所包含的專案內建置 BizTalk 組件，並將這些組件加入到定義於每一個專案之部署屬性內的 BizTalk 應用程式。 如果應用程式不存在，會予以建立。 組件和組件的資源 (稱為「成品」) 也會部署到群組的 BizTalk 管理資料庫中，您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台或其他工具來加以檢視和管理。 如需有關此步驟的詳細資訊，請參閱[如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)。  
  
4.  **加入所需的應用程式正確運作的成品。** 從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以輕鬆地修改應用程式來完成它，例如加入和移除成品，例如傳送和接收連接埠、 指令碼、 原則、 非 BizTalk.NET 組件，以及其他等等。 如需詳細資訊，請參閱[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)。  
  
5.  **將成品分解到多個應用程式。** 在開發過程中，為了方便起見，您可能已經將組件部署到單一應用程式。 您可能會為了各種理由，而想要將成品分解到多個應用程式中，然後再部署到實際執行環境。 如需建構應用程式的最佳作法的詳細資訊，請參閱[部署 BizTalk 應用程式的最佳作法](../core/best-practices-for-deploying-a-biztalk-application.md)。  
  
6.  **在方案中建立的所有應用程式的.msi 檔案，並在本機安裝它們。** 您可以使用提供的匯出精靈，從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台或 BTSTask 命令列工具來建立包含每個應用程式成品的.msi 檔案。 如需詳細資訊，請參閱[匯出 BizTalk 應用程式、 繫結和原則](../core/exporting-biztalk-applications-bindings-and-policies.md)。 如果您想要在本機電腦上執行此方案，並確認它可如預期般運作，您可以採取額外的步驟，也就是從 .msi 檔案安裝成品。 如需詳細資訊，請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。 確認此方案可如預期般運作。  
  
7.  **視需要請重新部署 BizTalk 組件。** 在開發和偵錯您的 BizTalk 組件，您可能需要將其重新佈署多次。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供簡易的機制，可以重新部署。 如需詳細資訊，請參閱[如何重新部署 BizTalk 組件從 Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md)。  
  
8.  **匯出繫結檔案，並將其加入回應用程式 （選擇性）。** 若要在稍後能夠更輕鬆地將應用程式匯入回開發環境，以便進行變更或新增，您可以先匯出每一個應用程式的繫結，然後將其加入回應用程式中，為這些繫結指定開發目標環境。 當您稍後在開發電腦上將應用程式 .msi 檔案匯入回 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，可以指定要套用這些繫結。 如需詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
9. **產生每個應用程式的.msi 檔案交給關閉到測試小組**。 當您完成開發及偵錯您的 BizTalk 方案後時，您可以使用匯出精靈或 BTSTask 來產生應用程式.msi 檔案中，如稍早在步驟 6 中所述。 您應該在開發環境中匯入這些檔案到不同的 BizTalk 群組、 加以安裝，，然後確認 方案如預期運作。 您可以再遞交給測試小組.msi 檔，他們可以使用匯入應用程式進入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]測試電腦上執行，以及並加以安裝，如中所述[BizTalk 應用程式部署的測試工作](../core/testing-tasks-for-biztalk-application-deployment.md).  
  
## <a name="see-also"></a>另請參閱  
 [應用程式部署工作](../core/application-deployment-tasks.md)