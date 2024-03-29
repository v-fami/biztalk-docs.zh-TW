---
title: 如何在 GAC 中安裝組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6afc2f81-fa28-4144-b4bd-21c8f35f2270
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52e843d74b5420f8973f9d3663cfd05210c26996
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752363"
---
# <a name="how-to-install-an-assembly-in-the-gac"></a>如何在 GAC 中安裝組件
手動安裝和解除安裝 BizTalk 組件在全域組件快取 (GAC) 使用隨附的 Gacutil 工具[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
 使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您可以從部署時，自動安裝在 GAC 中的 BizTalk 組件[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 將此選項設定中部署 BizTalk 專案屬性;請參閱[如何在 Visual Studio 中的 設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。 您不能用於非 BizTalk.NET 組件安裝在 GAC 中; 這個方法您必須以手動方式，本主題中所述安裝它們。  
  
> [!NOTE]
>  組件已部署到 BizTalk 應用程式之後，您也可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，指定這些組件的部署選項。 請參閱[如何修改 BizTalk 組件的部署選項](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md)，並[如何修改.NET 組件、 COM 元件、 檔案或 BAM 成品的部署選項](../core/modify-deployment-options-of-net-assembly-com-component-file-bam-artifact.md)。  
  
## <a name="prerequisites"></a>先決條件  
使用具有 GAC 「 寫入 」 權限的帳戶登入。 本機電腦上的「系統管理員」帳戶具有這項權限。  

  
## <a name="install-using-gacutil"></a>使用 gacutil 安裝
  
1.  將 BizTalk 組件複製到本機電腦。  
  
2.  開啟**Visual Studio 的開發人員命令提示字元**以系統管理員身分。  
  
3.  輸入以下內容：  
  
     `gacutil /i path_to_assembly_file /f`

    例如，輸入：  
    `gacutil /i c:\temp\filename.dll /f`
    
`/f`選項會覆寫任何現有的組件具有相同的組件名稱。 如需的 gacutil 命令和選項的詳細資訊，請輸入`gacutil /?`。 

## <a name="uninstall-using-gacutil"></a>使用 gacutil 解除安裝
解除安裝組件，從全域組件快取 (GAC) 就必須完全解除部署應用程式。 您可以自動化此程序。 部署到生產環境應用程式，撰寫自動解除安裝組件從 GAC 解除安裝應用程式時的前置處理指令碼。 請參閱[使用前置和後置處理指令碼自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。  
  
 您也可以使用指令碼來移除其他檔案和設定。 請參閱[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。  
 
#### <a name="using-the-windows-interface"></a>使用 Windows 介面  
  
1.  開啟至 systemdrive%\Windows\Assembly。  
  
2.  以滑鼠右鍵按一下包含您的應用程式，選取在每個組件檔案**解除安裝**，然後選取**是**確認。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟**Visual Studio 的開發人員命令提示字元**以系統管理員身分。 
  
2.  輸入以下內容：  
  
     `gacutil /u` \<*完整的組件名稱*\>  
  
     例如，輸入：  
     `gacutil /u "hello,Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"`
       
## <a name="see-also"></a>另請參閱  
 [從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)  
[解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md)   
 [如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md)   
 [如何從 BizTalk 群組刪除 BizTalk 應用程式](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)
 
