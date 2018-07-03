---
title: 如何安裝 BizTalk 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing, requirements
- installing, applications
- installing, warnings
- applications, installing
ms.assetid: 99ee0b1a-d46a-4fb6-802b-6827dc740418
caps.latest.revision: 56
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2dc973315d804aeec615b5f2591e07d3a6c26031
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997767"
---
# <a name="how-to-install-a-biztalk-application"></a>如何安裝 BizTalk 應用程式
本主題說明如何在本機電腦上安裝應用程式，方法是在 Windows 介面中按兩下應用程式的 Windows Installer (.msi) 檔案，或從命令列執行 msiexec。 您也可以啟動安裝精靈的 [匯入精靈] 的最後一個步驟中所述[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  

> [!CAUTION]
>  如果此應用程式已安裝在這台電腦上，您可選擇修復該應用程式。 只有此應用程式已安裝單一 .msi 時才支援修復。 如果您在這台電腦上為此應用程式安裝一個以上的 .msi，就不應該選取這個選項。 這是因為選取「修復」將復原在此 .msi 檔案之後所安裝之 .msi 檔案所做的任何變更，而使您的應用程式無法運作。  

 您必須先將應用程式安裝在會執行它的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上，才能讓應用程式融入運作。 安裝應用程式後，其資源會放置到本機檔案系統中。 視應用程式、其內容以及其組態而定，安裝也會執行下列動作：  

- 新增組件至全域組件快取 (GAC)  

- 安裝憑證及虛擬目錄  

- 新增元件至 Windows 登錄。  

- 如果 .msi 檔案中有前置或後置處理指令碼，則會執行這些指令碼。  

  如需背景資訊，請參閱 <<c0> [ 會發生什麼事成品期間安裝和解除安裝](../core/what-happens-to-artifacts-during-installation-and-uninstallation.md)。  

## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須使用具有本機檔案系統寫入權限的帳戶登入。 視應用程式中包含的項目而定，您可能還需要具有 Windows 登錄、GAC、憑證存放區以及 Internet Information Services 的寫入權限。 本機電腦上的「系統管理員」帳戶具有這些權限。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  

## <a name="considerations-for-installing-an-application"></a>安裝應用程式的考量  
 安裝應用程式時，您可考量下列事項：  

- **您也必須安裝此應用程式有相依性的任何應用程式。** 當您安裝與某個成品有相依性的應用程式時，例如包含在另一個應用程式中的 BizTalk 組件，您也必須安裝包含該成品的應用程式。 您必須完成這個動作後，才可執行該應用程式。 例如，如果應用程式 A 相依於應用程式 B 中的組件，您也必須安裝應用程式 b。接著，您也可以安裝應用程式 a。如需背景資訊，請參閱 <<c0> [ 相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。  

- **您應該停止您要更新的應用程式。** 如果您正在執行安裝來更新應用程式中的成品，則不需要停止應用程式，除非更新包含一或多個與現有組件相同版本的組件。 若為上述情況，您就必須停止應用程式後再安裝更新。 但是，Microsoft 建議您在任何情況下都先停止應用程式，除非您知道該項更新在執行時不會影響應用程式。 如需詳細資訊，請參閱 <<c0> [ 更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)。  

- **當您安裝相同的應用程式的多個.msi 檔案時，就會新增或移除程式 中所做的只有一個項目。** 舉例來說，您可以這樣做來更新現有的應用程式。 接著，您可使用 [新增或移除程式] \(在 [控制台]) 完全解除安裝該應用程式，包含所有已更新的項目。 請注意，不支援按兩下 .msi 檔案或使用 msiexec 來解除安裝應用程式。 如需詳細資訊，請參閱 <<c0> [ 如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md)。  

- **憑證必須存在於裝載傳送埠，才能執行應用程式的所有電腦上。** 「其他人」憑證存放區包含傳送埠使用的憑證。  

- **您可以將應用程式成品分解到不同的.msi 檔案進行安裝。** 您不需要將所有應用程式成品安裝在執行該應用程式的每台電腦上。 您可將應用程式成品的子集匯出到不同的 .msi 檔案，以安裝在不同的電腦上。 如需相關指示，請參閱 <<c0> [ 如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  

- **如果應用程式.msi 檔案包含虛擬目錄，必須在本機電腦上執行 Internet Information Services (IIS)。** 如果沒有，安裝就會失敗。  

- **如果應用程式包含具有相同名稱做為其中一個已存在於本機電腦上的虛擬目錄，從應用程式的資源會新增至它。** 否則，會建立該虛擬目錄。 任何與新增檔案相同名稱的現有檔案都會被覆寫。 此外，現有虛擬目錄的安全性設定不會變更，您應該確認這些設定是否夠安全。  

- **建立虛擬目錄的應用程式集區，然後再安裝應用程式。** 如果應用程式包含虛擬目錄，且 IIS 中不存在任何應用程式集區，您應該手動建立應用程式集區後再進行安裝。 這樣，虛擬目錄在安裝期間才可繫結至該應用程式集區。 如果您未建立應用程式，虛擬目錄在安裝時就會繫結至預設的應用程式集區。  

- **確定 BTSHttpReceive.dll 已註冊為處理常式對應網際網路資訊服務 (IIS) 7.0 與。** 如果您的應用程式會包含在順序中的虛擬目錄 HTTP 接收位置來運作，您必須這麼做。  

- **安裝包含 32 位元電腦上的 64 位元成品的應用程式時，您可能會遇到問題。** 如需詳細資訊，請參閱 <<c0> [ 如何將 64 位元成品新增至應用程式](../core/how-to-add-a-64-bit-artifact-to-an-application.md)。  

- **如果目標目錄長度超過 260 個字元，您可能會遇到的問題。** 如果在 MSI 封裝安裝期間指定之目標目錄中的字元數目超過 260 個字元，安裝就會失敗。 若要解決這個問題，請確定所指定的目標目錄字元數目未超過 260 個字元。  

- **您不應該重新放置安裝資料夾。** 一旦安裝應用程式之後，您就不應該重新放置安裝資料夾或其所包含的檔案。 如果您這樣做，之後又嘗試移除 (解除安裝) 該應用程式，移除作業就會失敗。 尤其，應用程式安裝資料夾包含 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所產生之執行移除所需的檔案。 您不應該重新命名、移動或移除這些檔案。 這些檔案包括：  

  -   ApplicationDefinition.adf  

  -   Microsoft.BizTalk.CustomInstaller.dll  

  -   Microsoft.BizTalk.CustomInstaller.InstallState  

> [!NOTE]
>  如果您在安裝作業完成之前將其取消，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會回復安裝，但在作業取消之前由前置或後置處理指令碼所執行的動作除外。  
> 
> [!IMPORTANT]
>  在安裝任何應用程式之前，請確定您已從信任的來源接收 .msi 檔案。 惡意使用者可能會將程式碼包含在 .msi 檔案中，而在您的系統或網路上造成嚴重的後果。  如需詳細資訊，請參閱 <<c0> [ 安全性和 Windows Installer](../core/security-and-windows-installer.md)。  
> 
>  如果應用程式包含使用 Web 服務的網站或協調流程，請注意虛擬目錄上的安全性設定，就是在應用程式匯出期間產生 .msi 檔案時生效的那些安全性設定，但在現有的虛擬目錄中除外，在此情況下，會使用現有的設定。 安裝應用程式之後，您應該確定設定是否符合安全性需求。  
> 
>  匯出應用程式時，會移除檔案和資料夾從 Alldiscretionary 存取控制清單 (Dacl)。 將應用程式安裝在主控件執行個體之後，您應該重新設定檔案和資料夾上的所有安全性設定，包括虛擬目錄。  

-   **您可能需要變更本機路徑： 參考由 HTTP 虛擬目錄目的地接收位置之後它會建立在目標電腦上。**  

     在目標電腦上建立虛擬目錄時，它會指向下列其中一個實體目錄：  

     \<*安裝磁碟機*\>\Program Files\Microsoft BizTalk Server\HttpReceive  

     \- **或**–  

     \<*安裝磁碟機*\>\Program 檔案 (x86) \Microsoft BizTalk Server\HttpReceive  

     如果 BizTalk HTTP 接收 ISAPI 延伸模組 BTSHTTPReceive.dll 不在指定的目錄中，或者目標電腦執行 64 位元作業系統，則您必須變更本機路徑：指向包含 BizTalk HTTP 接收 ISAPI 延伸模組檔案之實體目錄的虛擬目錄目的地。 例如，如果目標電腦執行 64 位元版本的 Windows Vista，則本機路徑： 虛擬目錄目的地應變更為\<安裝磁碟機\>\Program 檔案 (x86) \Microsoft BizTalk Server\HttpReceive64。  

## <a name="to-install-a-biztalk-application"></a>安裝 BizTalk 應用程式  

#### <a name="using-the-windows-interface"></a>使用 Windows 介面  

1. 將應用程式的 .msi 檔案複製到本機電腦。  

2. 如果您要重新安裝或升級現有的 BizTalk 應用程式，而且新的安裝包含具有相同的版本做為其中一個已存在於應用程式，或您要更新的成品與互動的組件，請確認應用程式已停止的應用程式資料夾上按一下滑鼠右鍵，然後按一下**停止**。  

3. 在 [Windows 檔案總管] 中，使用滑鼠右鍵按一下 .msi 檔案，啟動安裝精靈。  

4. 在 **選取安裝資料夾**頁面上，於**資料夾**，輸入 BizTalk 應用程式的完整安裝路徑。 範例：C:\Program Files\Generated by BizTalk\MyApplication。  

5. 按一下 **下一步**四次，然後在**安裝完成**頁面上，按一下**關閉**。  

6. 如果多台電腦將執行該應用程式，請在每台電腦上重複先前的步驟。  

    一旦將執行它的所有電腦上安裝應用程式和應用程式已匯入 BizTalk 群組，就可以開始從應用程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下 應用程式的資料夾，然後按一下**啟動**。 如需完整指示，請參閱 <<c0> [ 如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。  

#### <a name="using-the-command-line"></a>使用命令列  

1. 將應用程式的 .msi 檔案複製到本機電腦。  

2. 按一下 **開始**，按一下**執行**，型別`cmd`，然後按 ENTER 鍵。  

3. 瀏覽至儲存 .msi 檔案的位置。  

4. 輸入下列命令來安裝應用程式，提供適當的參數和值，如下表所示：  

   > [!IMPORTANT]
   >  僅支援下表中顯示的 msiexec 參數。  

    **msiexec** [**/i**]*封裝*[**/qn**] **TARGETDIR ="**<em>值</em>**"**]  

    範例： **msiexec /i MyApplication.msi**  


   |           參數           |                                                                                                 ReplTest1                                                                                                 |
   |-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |            **/i**             |                                                                                       安裝應用程式。                                                                                       |
   |           *封裝*           |                                                                              Windows Installer (.msi) 檔案的名稱。                                                                               |
   |            **/qn**            |                                                                    執行安裝，而不顯示使用者介面。                                                                     |
   | **TARGETDIR ="** *值* **"** | 指定應用程式安裝資料夾。 此值也可在 %BTAD_InstallDir% 環境變數中設定。<br /><br /> 範例：TARGETDIR="C:\Programs\BizTalk Applications\My Application" |


5. 如果多台電腦將執行該應用程式，請在每台電腦上重複先前的步驟。  

    將執行它的所有電腦上安裝應用程式之後，您可以開始從應用程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下 應用程式的資料夾，然後按一下**啟動**。 如需完整指示，請參閱 <<c0> [ 如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。  

## <a name="see-also"></a>另請參閱  
 [部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)   
 [如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md)