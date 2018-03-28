---
title: 附錄 a： 無訊息安裝 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94ded6b3-13ca-47e6-a038-254514f500e7
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c03568f86b8c3b609fed74a9faf7f6057614151c
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="appendix-a-silent-installation"></a>附錄 A：無訊息安裝
本主題列出建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無訊息安裝的步驟。  
  
## <a name="create-a-silent-installation"></a>建立無訊息安裝  
  
1.  依序按一下 [開始]、[所有程式] 及 [附屬應用程式]，然後按一下 [命令提示字元]。  
  
2.  前往安裝位置。 在命令提示字元中，輸入 `setup.exe /``<command name> <options>`，然後按 **ENTER**。 記錄檔會顯示安裝狀態。  
  
|命令名稱|選項|Description|  
|------------------|------------|-----------------|  
|/HELP 或 /? 或 /H||提供說明和快速參考。|  
|/QUIET||在安裝期間隱藏 UI - 所有對話方塊、錯誤，或需要使用者輸入的提示。 所有訊息都會輸入到安裝記錄檔。 **注意︰**您無法為升級指定 Quiet 旗標，因為升級會要求使用者確認選取的選項。|  
|/CABPATH|\<*封包檔位置*\>|指出可轉散發封包檔的位置。|  
|/S|\<*組態 XML 檔*\>|為指定組態檔中找到的功能，執行無訊息安裝。 **注意：**若要安裝所有功能，請針對組態 XML 檔的 `InstalledFeature` 參數指定 ALL 。|  
|/PASSIVE||執行被動式安裝。 安裝程式只會顯示進度列。|  
|/NORESTART||隱藏重新啟動提示，並在安裝結束後自動重新啟動。|  
|/FORCERESTART||安裝完成後，一律強制重新啟動。|  
|/PROMPTRESTART||重新啟動之前先提示使用者。|  
|/X 或 /UNINSTALL||解除安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。|  
|/L|\<Logfile\> [i][w][e][a][r][u][c][m][p][v][*]|將記錄資訊寫入指定路徑的記錄檔。 一律使用詳細的 Windows Installer 記錄，並附加到現有的檔案。<br /><br /> 下列旗標指出會記錄的資訊：<br /><br /> i - 狀態訊息<br /><br /> w - 非嚴重警告<br /><br /> e - 所有錯誤訊息<br /><br /> a - 啟動動作<br /><br /> r - 特定動作記錄<br /><br /> u - 使用者要求<br /><br /> c - 初始使用者介面參數<br /><br /> m - 記憶體不足<br /><br /> p - 終端機內容<br /><br /> v – 詳細資訊輸出<br /><br /> * - 全部|  
|/IGNOREDEPENDENCIES||略過可下載必要元件的檢查。|  
|/ INSTALLDIR \<*安裝路徑*\>|\<*程式檔案資料夾\>*|指定產品安裝位置的完整路徑。|  
|/COMPANYNAME|\<*公司名稱*\>|設定公司或組織名稱。|  
|/USERNAME|\<*使用者名稱*\>|設定使用者名稱。|  
|/ADDLOCAL ALL||安裝所有功能。 如需 ADDLOCAL 命令的詳細資訊，請參閱 [Listing of Values for the ADDLOCAL Command](http://go.microsoft.com/fwlink/p/?LinkID=189319) (ADDLOCAL 命令的值清單)。|  
|/REMOVE ALL||移除所有功能。|  
|/REPAIR ALL||修復所有功能。|  
|/CEIP||啟用客戶經驗改進計劃 (CEIP)|  
|/PRODUCT UDDI||安裝 UDDI|  
|msiexec.exe /i  [MSIPATH] INSTALLDIR=[INSTALLDIRPATH] DATADIR=[DATADIRPATH] SQLSERVERMACHINENAME=[SQLSERVERNAME] OVERWRITERFIDSTORE=1 INSTALLLEVEL=5 /lvxp RfidServicesInstall.txt /q<br /><br /> 例如：msiexec.exe /i "\\\ABC\XYZ\RFID_x86\RfidServices.msi" INSTALLDIR=“C:\Program Files\Microsoft BizTalk RFID\” DATADIR=“C:\Program Files\Microsoft BizTalk RFID\” SQLSERVERMACHINENAME=(local) OVERWRITERFIDSTORE=1 INSTALLLEVEL=5 /lvxp RfidServicesInstall.txt /q||安裝 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] RFID|  
  
 **其他**  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可使用自動化電子軟體散發，又稱為無訊息安裝。 無訊息安裝會：  
  
    -   在具有相同設定的電腦上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
    -   可讓系統管理員將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝在遠端電腦上，不需要使用者介入。  
  
    -   使用者不需要監控安裝和提供輸入。  
  
-   若要建立無訊息安裝，請使用命令列選項隱藏所有互動。  
  
-   當您完成無訊息安裝時，命令視窗中不會顯示任何訊息。 請使用安裝記錄檔檢閱狀態。  
  
