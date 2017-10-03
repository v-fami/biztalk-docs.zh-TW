---
title: "如何設定 IIS，HTTP 接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 64-bit support, HTTP adapters
- HTTP adapters, IIS
- configuring [HTTP adapters], IIS
- receive locations, IIS
- IIS, receive locations
- HTTP adapters, 64-bit support
- IIS, HTTP adapters
ms.assetid: 1c420f46-01f1-4c9c-9144-d8d2acc8b0c4
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1daa535c546bef0b390f0f7f84c45d546ac0005
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-iis-for-an-http-receive-location"></a>如何設定 HTTP 接收位置的 IIS
視您使用的 Microsoft Windows 版本而定，您必須以不同方式設定 Microsoft Internet Information Services (IIS) 來搭配使用 HTTP 配接器接收位置。  
  
 如果您的作業系統是[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]，IIS 7.0 提供兩種不同的應用程式隔離模式來保護 Web 應用程式。 背景工作處理序隔離模式是預設模式。 您可以設定 HTTP 配接器接收位置使用任一種模式，但建議使用工作者處理序隔離模式，因為它具有改善的安全性功能。  
  
> [!NOTE]
>  如果您的作業系統是 x64 版本的[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]，64 位元版本的 HTTP 接收配接器安裝到*\<磁碟機 >***\Program Files (x86) \Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\HttpReceive64**目錄您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]預設。 若要在 64 位元原生模式中執行 64 位元版本的 HTTP 接收配接器，您必須從命令列執行下列指令碼：  
>   
>  `cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`  
>   
>  `C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`  
  
> [!NOTE]
>  任何導致 SOAP 與 HTTP 共用相同程序的 IIS 組態都無效。 每個程序只能有一個隔離的接收器。  
  
### <a name="to-configure-the-iis-70-worker-process-isolation-mode-to-work-with-the-http-adapter-receive-location"></a>若要設定 IIS 7.0 背景工作處理序隔離模式，才能使用 HTTP 配接器接收位置  
  
1.  按一下**啟動**，指向 **設定**，然後按一下 **控制台**。  
  
2.  在控制台中，按兩下**系統管理工具**。  
  
3.  在 [系統管理工具] 中按兩下**Internet Information Services**。  
  
4.  在 [Internet Information Services] 中，選取根 Web 伺服器項目。 在**功能檢視**，連按兩下**處理常式對應**，然後在 動作 窗格中，按一下 **新增指令碼對應**。  
  
    > [!NOTE]
    >  在 Web 伺服器層級設定指令碼對應會使得此對應套用至所有子網站。 若要限制對應至特定網站或虛擬資料夾，請選取目標網站或資料夾，而不要選取 Web 伺服器。  
  
5.  在**新增指令碼對應**對話方塊中，於**要求路徑**欄位中，輸入`BtsHttpReceive.dll`。  
  
6.  在**可執行檔**欄位中，按一下省略符號 (**...**) 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive。 選取**BtsHttpReceive.dll** ，然後按一下 **確定**。  
  
7.  在**名稱**欄位中，輸入`BizTalk HTTP Receive`，然後按一下 **要求限制**。  
  
8.  在**要求限制**對話方塊中，按一下 **動詞**索引標籤，然後選取 **下列動詞命令的其中一個**。 輸入`POST`為動詞命令。  
  
9. 在**存取**索引標籤上，選取**指令碼**，然後按一下 **確定**。  
  
10. 當畫面上出現允許 ISAPI 擴充程式的提示時，請按一下 [是]。  
  
11. 以滑鼠右鍵按一下**應用程式集區**，指向 **新增**，然後按一下 **應用程式集區**。  
  
12. 在**新增應用程式集區**對話方塊中，於**名稱**方塊中，輸入應用程式集區的名稱。 選取**NET Framework v4.0.30319** ，然後按一下 **確定**。  
  
    > [!NOTE]
    >  版本號碼會根據電腦上安裝的.NET framework 版本而有所不同。  
  
     新的應用程式集區會出現在清單中**應用程式集區**。  
  
13. 在**應用程式集區**，請在**功能檢視**選取新的應用程式集區，然後按一下 [**進階設定**動作] 窗格中。  
  
14. 在**進階設定**對話方塊中，於**處理序模型**區段的**識別**欄位中，按一下省略符號 (**...**) 按鈕。  
  
15. 在**應用程式集區識別**對話方塊中，選取**自訂帳戶**，然後按一下 **設定**。 按一下 **[確定]** 以關閉 **[進階設定]** 對話方塊。  
  
16. 在 [IIS 管理員] 中，開啟**網站**資料夾。 以滑鼠右鍵按一下**Default Web Site** ，然後按一下 **新增應用程式**。  
  
17. 在**新增應用程式**對話方塊中，於**別名**，輸入別名，應用程式時，產生關聯，然後按一下 **選取**。  
  
18. 在**選取應用程式集區**對話方塊中，選取您稍早建立的新應用程式集區，然後按一下**確定**。  
  
19. 按一下省略符號 (**...**) 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive 的**實體路徑**。  
  
20. 按一下**連接身分**並輸入**使用者名**和**密碼**使用者帳戶是 Administrators 群組的成員，然後按一下 **確定**.  
  
21. 按一下**測試設定**並確認沒有錯誤，會顯示在**測試連接** 對話方塊。 按一下 [關閉]，然後按一下 [確定]。  
  
22. 新的應用程式會出現在清單中**預設的網站**在網際網路資訊服務 (IIS) 管理員 中。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 HTTP 接收位置](../core/how-to-configure-an-http-receive-location.md)