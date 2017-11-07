---
title: "步驟 5： 設定交易夥伴網頁 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38c3054d-932a-42b6-a821-8b30604d8426
caps.latest.revision: "38"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3f1dce6a68dc334f9f5f30b1aae938ada6f612a
ms.sourcegitcommit: 9aaed443492b74729171fef79c634bff561af929
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2017
---
# <a name="step-5-configure-the-trading-partner-web-pages"></a>步驟 5： 設定交易夥伴網頁
![步驟 5 之 11](../core/media/tut-step5-of-11.gif "Tut_Step5_of_11")  
  
 在此步驟中，您會執行下列工作來設定交易夥伴網頁：  
  
-   啟用 HTTP 傳輸所需的 BTS HTTP 接收 ISAPI 篩選器。  
  
-   設定資料夾及 aspx 頁，使用 HTTP 傳輸將 997 通知傳送至夥伴組織 Fabrikam。 Fabrikam 虛擬目錄會卸除到 997 通知\\_997ToFabrikam 資料夾，會在 997 傳送埠的 Destination_URL 設定中叫出。  
  
-   設定 ASPX 頁將原始訊息傳送至主要組織 Contoso。 Contoso 虛擬目錄會使用 BTSHttpReceive.dll 接收 AS2 訊息，並將它提交至接收位置。  
  
> [!NOTE]
>  本主題提供的程序是有關於 IIS 7.0。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-enable-the-bts-isapi-filter"></a>若要啟用 BTS ISAPI 篩選器  
  
1.  按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.  
  
2.  選取根 Web 伺服器項目和**功能檢視**，按兩下**處理常式對應**，然後在**動作**] 窗格中，按一下 [**新增的指令碼對應**.  
  
    > [!NOTE]
    >  在 Web 伺服器層級設定指令碼對應會使得此對應套用至所有子網站。 若要限制對應至特定網站或虛擬資料夾，請選取目標網站或資料夾，而不要選取 Web 伺服器。  
  
3.  在**新增指令碼對應**對話方塊方塊中，輸入`BtsHttpReceive.dll`中**要求路徑**欄位。  
  
4.  在**可執行檔**欄位中，按一下**省略符號 （...）**按鈕並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive。 選取**BtsHttpReceive.dll**，然後按一下 **確定**。  
  
5.  輸入`BizTalk HTTP Receive`中`Name`欄位，，然後按一下**要求限制**。  
  
6.  在**要求限制**對話方塊中，選取**動詞**索引標籤，然後選取 **下列動詞命令的其中一個**。 輸入`POST`為動詞命令。  
  
7.  在**存取**索引標籤上，選取**指令碼**，然後按一下 **確定**。  
  
8.  按一下**確定**時提示您允許 ISAPI 延伸模組，請按一下 **是**。  
  
9. 以滑鼠右鍵按一下 [BTSHttpReceive.dll] 項目，然後選取**編輯功能權限**。  
  
10. 請確認**讀取**，**指令碼**和**Execute**已選取，然後再按一下**確定**。  
  
11. 按一下**功能檢視**，然後按兩下**ISAPI 及 CGI 限制**。  
  
12. 請確認 BTSHTTPReceive.dll 項目存在，而且**限制**設**允許**。  
  
    > [!NOTE]
    >  當您建立指令碼對應時，會自動建立 BTSHTTPReceive.dll 的 [ISAPI 及 CGI 限制] 項目。  
  
### <a name="to-configure-the-fabrikam-web-page"></a>若要設定 Fabrikam 網頁  
  
1.  在 [IIS 管理員] 中，以滑鼠右鍵按一下**應用程式集區**選取**新增應用程式集區**。  
  
2.  在**新增應用程式集區**對話方塊方塊中，輸入**BizTalkAppPool**中**名稱**，然後選取**.NET Framework v4.0.30210**中**.NET framework 版本**下拉式清單。 按一下 **[確定]**。  
  
    > [!NOTE]
    >  版本號碼可能會依據電腦上安裝的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 版本而有所不同。  
  
3.  選取**應用程式集區**，請在**功能檢視**選取**BizTalkAppPool**，然後按一下 **進階設定**中**動作**窗格。  
  
4.  在**進階設定** 對話方塊中，將**啟用 32 位元應用程式**至**True**。  
  
    > [!NOTE]
    >  如果您希望在 64 位元的電腦上以 32 位元模式執行 IIS，才需要此步驟。  
  
5.  選取**識別**，然後按一下 [**省略符號 （...）** ] 按鈕。  
  
6.  在**應用程式集區識別**對話方塊中，選取**自訂帳戶**，然後按一下 **設定**。  
  
7.  輸入**使用者名**和**密碼**是 administrators 群組的成員的使用者帳戶，請輸入中的密碼**確認密碼**然後按一下  **確定**傳回給 IIS Manager 中的三倍。  
  
8.  在 [IIS 管理員] 中，開啟**網站**資料夾。 以滑鼠右鍵按一下**Default Web Site**，然後選取**新增應用程式**。  
  
9. 在**新增應用程式**對話方塊方塊中，輸入**Fabrikam**中**別名**，然後按一下 **選取**。  
  
10. 中**選取應用程式集區**對話方塊中，選取**BizTalkAppPool**按一下**確定**。  
  
11. 按一下**省略符號 （...）**按鈕並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 tutorial\fabrikam 做為**實體路徑**。  
  
12. 按一下**測試設定**並確認沒有顯示在錯誤**測試連接** 對話方塊。 按一下 [關閉]，然後按一下 [確定]。  
  
13. 在 [IIS 管理員] 中，選取 Fabrikam 虛擬目錄和**功能檢視**，連按兩下**驗證**。  
  
14. 在**驗證**，選取**匿名驗證**並確認**狀態**是**啟用**。 如果**狀態**是**已停用**，按一下 **啟用**中**動作**窗格。  
  
### <a name="to-configure-the-contoso-web-page"></a>若要設定 Contoso 網頁  
  
1.  在 [IIS 管理員] 中，開啟**網站**資料夾。 以滑鼠右鍵按一下**Default Web Site** ，然後選取 **新增應用程式**。  
  
2.  在**新增應用程式**對話方塊方塊中，輸入**Contoso**中**別名**，然後按一下 **選取**。  
  
3.  中**選取應用程式集區**對話方塊中，選取**BizTalkAppPool**按一下**確定**。  
  
    > [!NOTE]
    >  BizTalkAppPool 在之前設定 Fabrikam 網頁時就已建立，且應設為屬於系統管理員群組成員之使用者的識別。  
  
4.  按一下**省略符號 （...）**按鈕並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive 的**實體路徑**。  
  
5.  按一下**測試設定**並確認沒有顯示在錯誤**測試連接** 對話方塊。 按一下 [關閉]，然後按一下 [確定]。  
  
6.  在 [IIS 管理員] 中，選取 Contoso 虛擬目錄和**功能檢視**，連按兩下**驗證**。  
  
7.  在**驗證**，選取**匿名驗證**並確認**狀態**是**啟用**。 如果**狀態**是**已停用**，按一下 **啟用**中**動作**窗格。  
  
## <a name="next-steps"></a>後續步驟  
 設定的接收位置 (**Receive_AS2**) 中所述，從 Fabrikam 接收 AS2 訊息[步驟 6： 設定 EDI AS2 接收位置](../core/step-6-configure-the-edi-as2-receive-location.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)
