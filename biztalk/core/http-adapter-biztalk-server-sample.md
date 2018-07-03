---
title: HTTP 配接器 （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: f3bd8172-15c4-42fa-aa17-e4bed9d4aba4
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4002fa7c1b310f5b77806eb0f1b222c015cd989
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023204"
---
# <a name="http-adapter-biztalk-server-sample"></a>HTTP 配接器 （BizTalk Server 範例）
HTTP 配接器範例會示範如何實作用於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的「要求/回應」和「請求/回應」範例。  

## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>* \AdaptersDevelopment\HttpAdapter\  

 下表顯示此範例中的檔案，並描述其用途。  

|檔案|描述|  
|---------------|-----------------|  
|\Design-Time\Adapter Management|包含實作此配接器之設計階段部分的專案。|  
|\Run-Time\HttpReceive|包含實作要求/回應配接器通訊模式的專案。 這是外掛式接收器。|  
|\Run-Time\HttpSend|包含實作請求/回應配接器通訊模式的專案。|  

## <a name="how-to-use-this-sample"></a>如何使用此範例  
 這個範例是要做為您用來開發自訂配接器的架構。 在某些情況下，BizTalk Server 可能需要訊息傳輸到特定的自訂應用程式，或使用的通訊協定的原生的配接器不存在。 有些協力廠商有撰寫配接器以支援其他的通訊協定。 在決定要撰寫自訂配接器之前，您必須判斷是否有適用於通訊協定的配接器。 如果您找不到支援您通訊需求的配接器，即可開發自己的自訂配接器。  

 撰寫自訂配接器可能會是具有挑戰性的工作。 為了簡化這項程序，Microsoft 開發了稱為「配接器架構」的基礎。 您可以使用此架構為基礎，您的開發，以及 BizTalk Server SDK 中的範例配接器程式碼。  如需有關自訂配接器以及配接器架構的詳細資訊，請參閱**另請參閱**這份文件結尾的區段。  

## <a name="building-and-initializing-the-sample-adapter"></a>建置和初始化範例配接器  

> [!IMPORTANT]
>  如果 BizTalk 安裝是 64 位元，或安裝位置已有修改，則需要隨之變更 OutboundAssemblyPath、InboundAssemblyPath、AdapterMgmtAssemblyPath。  

#### <a name="to-build-and-initialize-the-http-adapter-sample"></a>若要建置和初始化 HTTP 配接器範例  

1. 在命令視窗中，瀏覽至下列資料夾：  

    \<*範例路徑*\>\AdaptersDevelopment\HttpAdapter  

2. 執行檔案 Setup.bat，這會執行下列動作：  

   -   編譯 HTTP 配接器及其所有相依性。  

   -   建立由配接器的接收者端所使用 Internet Information Services (IIS) 應用程式。  

   在 IIS 7.0 上，您必須確定正在執行此 IIS 應用程式之應用程式集區的識別屬於下列群組的成員：  

-   BizTalk 外掛式主控件使用者群組。  

-   IIS_WPG 群組。  

-   在 IIS 7.0 上，您必須移轉應用程式，才能使其在整合式 .NET 模式下運作。 您可以移轉應用程式組態，包括的內容\<httpHandlers\>組態 區段中的，使用下列從命令列視窗 （視窗必須以系統管理員身分執行）：  

    ```  
    %systemroot%\system32\inetsrv\APPCMD.EXE migrate config "Default Web Site/HttpReceive"  
    ```  

-   在移轉應用程式之後，該應用程式便會在「一般」與「整合式 .NET」兩種模式下執行，而且也會在下層的平台上執行。  

> [!NOTE]
>  在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。  

> [!NOTE]
>  若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 使用此金鑰組簽署所產生的組件。  

> [!NOTE]
>  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  

## <a name="registering-the-sample-adapter"></a>註冊範例配接器  

#### <a name="to-register-the-http-adapter-sample"></a>若要註冊此 HTTP 配接器範例  

1. 在 Windows 檔案總管中，瀏覽至安裝磁碟機[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，然後瀏覽至\<範例路徑\>\AdaptersDevelopment\HTTPAdapter。  

2. 若要將範例配接器新增至登錄中，按兩下**HTTP.NET.reg**。  

   > [!NOTE]
   >  HTTP.NET.reg 包含硬式編碼路徑[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝目錄。 如果您未安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在預設位置或升級您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來自舊版本的安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須修改檔案 HTTP.NET.reg 適當的路徑。 更新與 "OutboundAssemblyPath" 和 "AdapterMgmtAssemblyPath" 值關聯的路徑，使它們指向特定檔案的正確位置。  
   > 
   > [!IMPORTANT]
   >  如果您在 64 位元電腦上安裝 BizTalk，可將所有 HKEY_CLASSES_ROOT\CLSID\ 登錄項目執行個體都變更為 hkey_classes_root\wow6432node\clsid \ 中**HTTP.NET.reg**登錄檔。  

3. 在 **登錄編輯程式**  對話方塊中，按一下**是**以將範例配接器新增至登錄，然後按一下**確定**。  

4. 若要在關閉 Windows 檔案總管中，**檔案**功能表上，按一下**關閉**。  

## <a name="installing-the-sample-adapter"></a>安裝範例配接器  

#### <a name="to-install-the-http-adapter-sample"></a>若要安裝此 HTTP 配接器範例  

1. 按一下 **開始**功能表上，選取**所有程式**，選取[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後選取**BizTalk Server 管理**。  

2. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]樹狀結構，然後展開**BizTalk 群組**樹狀結構，然後展開**平台設定**樹狀目錄中。  

3. 以滑鼠右鍵按一下**配接器**，按一下**新增**，然後按一下**配接器**。  

4. 在 **配接器屬性**對話方塊方塊中，執行下列動作。  


   |  使用   |                  以進行此動作                  |
   |-------------|----------------------------------------------|
   |    [屬性]     |              型別**HTTP.NET**。              |
   |   配接器   | 選取  **HTTP.NET**從下拉式清單。 |
   | 描述 |      型別**範例 HTTP.NET 配接器**。       |


5. 按一下 [確定] 。  

6. 配接器隨即會出現在 BizTalk 管理主控台右側視窗的配接器清單中。  

## <a name="stopping-and-restarting-the-host-instance"></a>停止並重新啟動主控件執行個體  

#### <a name="to-stop-and-restart-the-host-instance-for-the-http-adapter-sample"></a>若要停止並重新啟動 HTTP 配接器範例的主控件執行個體  

1. 按一下 **開始**功能表上，選取**所有程式**，選取[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後選取[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。  

2. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]樹狀結構，然後展開**平台設定**，然後按一下**主控件執行個體**。  

3. 在 [結果] 窗格中，以滑鼠右鍵按一下主控件執行個體 （通常是電腦名稱），，然後按一下**停止**。  

    主控件執行個體狀態會變更為**已停止**。  

4. 在 [結果] 窗格中，以滑鼠右鍵按一下主控件執行個體，然後**啟動**。  

   現在，您的應用程式可開始使用 HTTP.NET 配接器。 設定配接器，格式**虛擬目錄**傳輸屬性屬於表單： /httpreceive/httpreceive.aspx?optionalQueryString。  

## <a name="comments"></a>註解  
 中提供的 BaseAdapter 類別使用 HTTP.NET 配接器可讓*\<範例路徑\>* \AdaptersDevelopment\BaseAdapter\v1.0...2\\。 這些提供於 BaseAdapter 專案中的類別是為了加速配接器的開發。 如需所提供類別的詳細資料，請參閱 BaseAdapter 程式碼註解。  

## <a name="see-also"></a>另請參閱  
 [註冊配接器](../core/registering-an-adapter.md)   
 [配接器範例-用法](../core/adapter-samples-usage.md)   
 [開發自訂配接器](../core/developing-custom-adapters.md)   
 [什麼是配接器架構？](../core/what-is-the-adapter-framework.md)   
 [使用配接器架構工具](../core/using-the-adapter-framework-tools.md)   
 [開發接收配接器](../core/developing-a-receive-adapter.md)   
 [開發傳送配接器](../core/developing-a-send-adapter.md)   
 [如何部署自訂配接器](../core/how-to-deploy-a-custom-adapter.md)   
 [設計您的配接器的秘訣](../core/tips-for-designing-your-adapter.md)   
 [配接器設計階段設定](../core/adapter-design-time-configuration.md)