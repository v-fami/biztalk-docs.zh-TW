---
title: 如何連結到讀我檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- linking, readme files
- applications, readme files
- linking, applications
- applications, linking
ms.assetid: 7ddbfe77-c8b5-4f90-80ee-8fd5ba57170b
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20bc84909c4bb9938556edafee1bd671ab97ab7d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981071"
---
# <a name="how-to-link-to-a-readme-file"></a>如何連結到讀我檔案
本主題說明如何使用 BizTalk Server 管理主控台或命令列加入 Readme.htm 檔案，以便使用者按一下 [控制台] 中 [新增或移除程式] 的連結時會出現這個檔案。  
  
 安裝 BizTalk 應用程式時，會在 [控制台] 的 [新增或移除程式] 中自動建立名為 Readme.htm 檔案的連結。 如果 Readme.htm 檔案存在於應用程式的安裝資料夾中，使用者可以開啟它在您的應用程式的名稱下按一下出現的 「 按一下這裡取得支援資訊 」 連結，然後按一下 "%BTAD_InstallDir%\Readme.htm"。 （%btad_installdir%是環境變數代表應用程式安裝資料夾）。  
  
 若要讓 [控制台] 中 [新增或移除程式] 的 Readme.htm 檔案連結正常運作，您必須執行下列動作：  
  
- 指定 Readme.htm 檔案的名稱。  
  
- 將 Readme.htm 加入至應用程式時，請將應用程式安裝資料夾指定為此檔案的目的地位置 (如底下的步驟 6 所述)。 預設的應用程式安裝資料夾是 %ProgramFiles%\Generated by BizTalk\ApplicationName。 您可以將此路徑表示為 %BTAD_InstallDir%。  
  
  如果您想要覆寫應用程式中現有的 Readme.htm 檔案，請指定 [覆寫] 選項。 如果沒有選取此選項，而且 Readme.htm 檔案已經存在應用程式中，則加入作業會失敗。  
  
> [!NOTE]
>  如果您針對這個應用程式安裝多個 .msi 檔案，而且為每個 .msi 檔案指定不同的安裝路徑，當使用者按一下 [新增或移除程式] 中的 [讀我檔案] 連結時，會開啟最後安裝之 .msi 檔案中包含的 Readme.htm 檔案。  
  
> [!IMPORTANT]
>  如果您沒有建立讀我檔案，並依照本主題所述將它加入至應用程式，當使用者按一下 [讀我檔案] 連結時，就不會出現任何檔案。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-add-a-readme-file-to-an-application"></a>若要將讀我檔案加入至應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]和包含您要在其中新增 Readme.htm 檔案的應用程式的 BizTalk 群組。  
  
3. 依序展開**應用程式**和您要在其中新增 Readme.htm 檔案的應用程式。  
  
4. 以滑鼠右鍵按一下**資源**資料夾，指向**新增**，然後按一下**資源**。  
  
5. 按一下 **新增**，選取 Readme.htm 檔案，然後按一下 **開啟**。  
  
6. 在 **目的地位置**，，如下所示指定預設情況下，應用程式安裝資料夾的完整路徑: %BTAD_InstallDir%\Readme.htm。 您不應該變更此路徑。 如果未提供應用程式安裝資料夾的正確路徑，安裝期間就不會將檔案複製到此位置，而且連結也不會作用。  
  
7. 完成後，請按一下 **[確定]**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2. 輸入下列命令，並以適當的值替代，如下表所述：  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>值</em>] **/Type:System.BizTalk:File** [**/覆寫**] **/Source:**<em>值</em>[**/Destination:**<em>值</em>] [**/Server:** <em>值</em>] [**/database:**<em>值</em>]  
  
    範例  
  
    **BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:File / 覆寫 /Source:"C:\Readme Files\MyApplication\Readme.htm"/Destination:%BTAD_InstallDir%\Readme.htm"/Server:MyServer /Database:BizTalkMgmtDB**  
  
   |參數|ReplTest1|  
   |---------------|-----------|  
   |**/ 應用程式名稱**|加入讀我檔案的 BizTalk 應用程式名稱。 如果沒有指定應用程式名稱，將會使用預設的 BizTalk 應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
   |**/ 類型**|System.BizTalk:File (此值不區分大小寫)。|  
   |**/ 覆寫**|覆寫現有檔案的選項。 若未指定此選項，且應用程式中現有的檔案與所加入的檔案同名，AddResource 作業將會失敗。|  
   |**/ 來源**|來源檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
   |**/ 目的地**|%BTAD_InstallDir%\Readme.htm<br /><br /> 這表示應用程式安裝資料夾和 Readme.htm 檔案的完整路徑，而且是安裝期間 Readme.htm 檔案複製的目的地位置。 如果未提供此路徑，就不會將檔案複製到應用程式安裝資料夾，而且 [新增或移除程式] 中的 Readme.htm 連結也不會作用。|  
   |**/ 伺服器**|裝載 BizTalk 管理資料庫的 SQL Server 執行個體名稱。 如果您指定 Database 參數，則為必要項。 如果不提供名稱，則會採用 localhost。 如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。|  
   |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果您指定 Server 參數，則為必要項。 如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)   
 [AddResource 命令：檔案](../core/addresource-command-file.md)