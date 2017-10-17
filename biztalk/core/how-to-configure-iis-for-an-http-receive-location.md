---
title: "HTTP 接收位置設定 IIS |Microsoft 文件"
description: "在 IIS 中，建立 BTS HTTP 接收應用程式和 BizTalk Server 中的測試應用程式集區設定"
ms.custom: 
ms.date: 10/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c420f46-01f1-4c9c-9144-d8d2acc8b0c4
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e09768d6616a33a4900995f3dd3225fa34318b3c
ms.sourcegitcommit: 75d35f6f230f0846c29a4b146c6d5b074e60b13c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2017
---
# <a name="configure-iis-for-an-http-receive-location"></a>HTTP 接收位置設定 IIS
HTTP 接收位置所使用的網際網路資訊服務 (IIS) 中的應用程式。 本主題列出的步驟來啟用 HTTP 接收位置在 IIS 中。 

根據您的作業系統，設定 IIS 應用程式的步驟可能會改變。 做為指南，使用下列步驟，因為使用者介面可能會在您的作業系統上的不同。
  
## <a name="32-bit-vs-64-bit"></a>32 位元與 64 位元

HTTP 接收位置會使用 BTSHTTPReceive.dll。 沒有 32 位元和 64 位元版本的 dll。 您選擇您想要使用哪個的版本。 64 位元處理序會有更多可用的記憶體，因此如果您處理大型訊息，則為 64 位元版本可能是最佳。 

**32 位元的安裝位置**: *Program Files (x86) \Microsoft BizTalk Server\HttpReceive*。
**64 位元的安裝位置**: *Program Files (x86) \Microsoft BizTalk Server\HttpReceive64*

若要執行 64 位元版本的 HTTP 接收配接器在 64 位元原生模式中，開啟命令提示字元，並執行下列指令碼：  

1. 類型：`cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`  

2. 類型：`C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`  
  
> [!NOTE]
>  任何導致 SOAP 與 HTTP 共用相同程序的 IIS 組態都無效。 每個程序只能有一個隔離的接收器。  
  
##  <a name="configure-the-iis-application"></a>設定 IIS 應用程式
  
1.  開啟**Internet Information Services** (開啟**伺服器管理員**，選取**工具**，然後選取**Internet Information Services 管理員**). 
  
2.  在 IIS 中，選取您的伺服器名稱。 在**功能檢視**，連按兩下**處理常式對應**。 在 [動作] 窗格中，選取**新增指令碼對應**。  
  
    > [!NOTE]
    >  當您在 web 伺服器層級設定指令碼對應時，對應適用於所有網站。 如果您想要限制對應至特定網站或虛擬資料夾，選取該網站或資料夾，然後再新增 指令碼對應。  
  
3.  在**新增指令碼對應**，選取**要求路徑**，然後輸入`BtsHttpReceive.dll`。  
  
4.  在**可執行檔**，選取省略符號 (**...**)，並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive。 選取**BtsHttpReceive.dll**，然後選取**開啟**。  
  
5.  在**名稱**，輸入`BizTalk HTTP Receive`，然後選取**要求限制**。 在這個視窗：
  
    1. 在**動詞**，選取**下列動詞命令的其中一個**，並輸入`POST`。  
  
    2. 在**存取**，選取**指令碼**，然後選取**確定**。  
  
    3. 當提示您允許 ISAPI 延伸模組，請選取**是**。  
  
6. 建立新的應用程式集區 (以滑鼠右鍵按一下**應用程式集區**，選取**新增應用程式集區**)。 **名稱**應用程式集區 (例如`BTSHTTPReceive`)，請選取**NET Framework v4.0.30319**，然後選取**確定**。  
  
    > [!NOTE]
    >  .NET 版本號碼會根據電腦上安裝的.NET framework 版本而有所不同。  
  
     會列出新的應用程式集區。  
  
7. 選取新的應用程式集區，然後開啟**進階設定**(**動作**窗格)。 在這個視窗：

    - **啟用 32 位元應用程式**： 設為**True**如果您選擇 32 位元**BtsHttpReceive.dll**
    - **處理模型** 區段中，**識別**： 選取省略符號 (**...**)，請選取**自訂帳戶**，然後**設定**其成員的帳戶**BizTalk Isolated Host Users**和**IIS_WPG**群組。 選取 [確定]。 
  
8. 加入新的應用程式的網站 (以滑鼠右鍵按一下**Default Web Site**，選取**新增應用程式**)。 在這個視窗：
  
    1. **別名**： 輸入您與應用程式產生關聯的別名 (例如`BTS HTTP Receive`，然後**選取**。  
    2. 選取您剛才新增的應用程式集區建立，然後再選取**確定**。  
    3. **實體路徑**： 選取省略符號 (**...**)，並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive。  
    4. **測試設定**以確認有無錯誤**測試連接** 對話方塊。 **關閉**，然後選取**確定**。  
  
    > [!TIP]
    > 如果測試設定會傳回警告，權限給資料夾或存取權的群組，可能會遺失應用程式集區身分識別。 做為疑難排解的步驟中，選取**連接身分**，輸入**使用者名稱**和**密碼**是 Administrators 群組的成員的使用者帳戶。 

9. 新的應用程式顯示的是列在**預設的網站**。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 HTTP 接收位置](../core/how-to-configure-an-http-receive-location.md)
