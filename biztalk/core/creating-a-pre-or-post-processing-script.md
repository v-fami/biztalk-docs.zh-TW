---
title: 建立前置或後置處理指令碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts, post-processing
- scripts, pre-processing
- scripts, warnings
- scripts, applications
- applications, scripts
- scripts, deploying
- deploying, scripts
ms.assetid: d5fbaec8-fbfe-4ceb-8ba8-0933baa37a1f
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 532c730d5a654512610a37c9dac783fbc6a76d6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239294"
---
# <a name="creating-a-pre--or-post-processing-script"></a>建立前置或後置處理指令碼
您可以在部署應用程式時建立指令碼來執行動作，然後定義該指定碼在部署階段的執行時機。 您可以利用環境變數來分隔程式碼，以便在同一個指令碼中同時包含安裝與清除程式碼。 您也可以將命令列引數傳送至指令碼中。  
  
> [!CAUTION]
>  當您編寫生產系統所使用的指令碼時，應該永遠採用無訊息模式。 那是因為等候使用者輸入動作的指令碼將會造成 BizTalk 資料庫在接收到使用者的輸入之前呈現鎖定而無法存取的狀態。  
  
## <a name="specifying-when-a-script-will-run-during-deployment"></a>指定指令碼在部署時的執行時機  
 當您將指令碼當作 System.BizTalk:PreProcessingScript (前置處理指令碼) 或者 System.BizTalk:PostProcessingScript (後置處理指令碼) 新增到應用程式時，即指定了指令碼的執行時機。  
  
 前置與後置處理指令碼執行時機如下：  
  
-   前置處理指令碼會在匯入或者安裝階段開始時執行。  
  
-   後置處理指令碼會在匯入或者安裝階段結束時執行。  
  
-   在解除安裝階段，所有的指令碼都會依據安裝時的程序順序倒退執行。 因此，後置處理指令碼會在開始解除安裝時執行，而前置處理指令碼則是在解除安裝結束時執行。  
  
-   如果安裝程序失敗，所有的指令碼將會按照適當的回復動作，進行反向呼叫。  
  
 一旦叫用，前置或後置處理指令碼會決定哪些部署狀態 （安裝、 匯入、 刪除、 解除安裝、 匯入回復或安裝回復） 中執行檢查環境變數 BTAD_ChangeRequestAction、 BTAD_InstallMode與 BTAD_HostClass 中所述[如何環境變數指出部署狀態](../core/how-environment-variables-indicate-deployment-state.md)。 如需變數的參考資訊，請參閱[前置和後置處理指令碼環境變數](../core/pre-and-post-processing-script-environment-variables.md)。  
  
 如需應用程式中加入指令碼的指示，請參閱[如何新增前置或後置處理指令碼至應用程式](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)。  
  
> [!NOTE]
>  如果您想要將命令列引數包含在指令碼中，必須使用 AddResource 命令來新增指令碼，本文稍後將會討論。  
  
## <a name="supported-script-file-extensions"></a>支援的指令碼檔案副檔名  
 支援的指令碼檔案副檔名如下：.com、.exe、.bat、.cmd、.vbs、.vbe、.js、.jse、.wsf 以及 .wsh。 此副檔名集合是在 PATHEXT 環境變數中定義。  
  
## <a name="logging-errors"></a>記錄錯誤  
 您應該採用的最佳作法是，設定每個指令碼將錯誤記錄到檔案中。 這是因為 Windows Installer 無法將指令碼產生的錯誤記錄起來。 在指令碼執行完畢之後，您應該檢查這些日誌，看看是否有任何需要修正的錯誤。  
  
 為了協助您判斷錯誤發生的時間，您可以在日誌檔案中加入日期與時間欄位。  
  
 使用下列程式碼來指定日誌檔案，然後記錄一個錯誤到該日誌。  
  
 `Set LogFile=<full path of log file>`  
  
 `…`  
  
 `echo %DATE% %TIME% <text> >> %LogFile%`  
  
 在下列範例中，如果沒有定義公開金鑰 Token，則會在指定的日誌檔案中加入一個項目。 在日誌檔案中，資料與時間會與 "Public key should be set in script" 文字寫在同一行中。  
  
 `set LogFile=C:\ScriptLog.txt`  
  
 `set PublicKeyToken=e5fd0ea4ecd37420`  
  
 `if not defined PublicKeyToken (`  
  
 `echo %DATE% %TIME% Public key should be set in script >> %LogFile%`  
  
 您也可以將 `exit /b 1` 新增到指令碼以便為 Windows Installer 產生錯誤程式碼，如此一來 Windows Installer 就會進行回復動作。  
  
 在下列範例中，如果沒有定義公開金鑰 Token，則指令碼會將錯誤傳回至 Windows Installer，導致 Windows Installer 進行回復動作。  
  
 `set LogFile=C:\ScriptLog.txt`  
  
 `set PublicKeyToken=e5fd0ea4ecd37420`  
  
 `if not defined PublicKeyToken (`  
  
 `echo %DATE% %TIME% Public key should be set in script >> %LogFile%`  
  
 `exit /b 1`  
  
## <a name="including-installation-and-cleanup-code-in-the-same-script"></a>同一個指令碼中同時包含安裝與清除程式碼  
 因為指令碼在安裝與解除安裝階段會以完全相反的順序執行，您可以將安裝與清除程式碼納入相同指令碼中的條件陳述式裡。 例如，您可以將安裝程式碼置於用來檢查安裝模式的條件陳述式裡，如下所示：  
  
```  
  
%BTAD_ChangeRequestAction%=Update AND %BTAD_InstallMode%=Install  
  
```  
  
 您可以在用來檢查安裝模式的條件陳述式中限定其清除程式碼，如下所示：  
  
```  
  
%BTAD_ChangeRequestAction%=Delete AND %BTAD_InstallMode%=Uninstall  
  
```  
  
## <a name="passing-in-command-line-arguments"></a>傳送命令列引數  
 當您使用 BTSTask AddResource 命令將指令碼新增到應用程式時，可以指定下列參數將命令列引數傳送至指令碼中。 如果您這麼做，當叫用指令碼時，引數就會傳送至指令碼中。  
  
 **/Property:Args =**"*引數清單*"  
  
> [!NOTE]
>  如果您的應用程式中有多個前置或後置處理指令碼，則這些指令碼沒有特定的執行順序。  
  
> [!IMPORTANT]
>  您應該避免在指令碼中使用 BTSTask 命令 (特別是那些會在匯入時執行的指令碼)，因為在同一個交易中，不同的指令碼不會被登記成匯入動作來處理。  
  
 如需使用 AddResource 命令加入至應用程式的指令碼的指示，請參閱[AddResource 命令： 前置處理指令碼](../core/addresource-command-preprocessing-script.md)。 另請參閱[AddResource 命令： 後置處理指令碼](../core/addresource-command-postprocessing-script.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用前置和後置處理指令碼自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)   
 [範本 （應用程式部署範例）](../core/template-application-deployment-sample.md)