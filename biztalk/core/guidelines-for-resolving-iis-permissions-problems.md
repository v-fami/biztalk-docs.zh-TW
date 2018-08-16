---
title: 解決 IIS 權限問題的指導方針 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting
ms.assetid: d9793a90-3aa3-46ab-a317-6d1e0fbfc1ef
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb91509ec3ad1c329190c848c25a60434f93499e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970572"
---
# <a name="guidelines-for-resolving-iis-permissions-problems"></a>解決 IIS 權限問題的指導方針
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在使用 HTTP、SOAP 和 Windows SharePoint Services 配接器時，會大量使用 Microsoft Internet Information Services (IIS) 以提供 Web 服務支援。  
  
 瞭解 IIS 實作應用程式的方式，將有助於 IIS 權限問題的疑難排解。  
  
 IIS 提供相關功能，供您建立 IIS 應用程式，做為在各自記憶體空間中執行的不同主控件程序。 一旦您建立的 IIS 應用程式主機，然後您必須定義兩組權限，IIS 應用程式主機**處理序識別**和 IIS 應用程式主機**使用者存取權限**。 在疑難排解 IIS 權限問題時，您應該檢查這兩組權限。  
  
> [!NOTE]
>  **處理序識別**和**使用者存取權限**也稱為**安全性內容**IIS 應用程式主機處理序。  
  
 本主題描述如何設定**處理序識別**和**使用者存取權限**IIS 應用程式主機處理程序，並提供解決 IIS 權限問題的一些一般指導方針。  
  
## <a name="setting-iis-application-host-process-identity"></a>設定 IIS 應用程式主控件程序識別  
 IIS 應用程式主控件程序的組態可能會隨著主控件程序所提供的功能層級而有所差異。 例如，只提供靜態 HTML 頁面的 IIS 應用程式主控件程序，其組態通常與提供 ASP 頁面或 ASP.NET 應用程式的 IIS 應用程式主控件程序不同。  
  
 IIS 應用程式主控件程序的組態也會隨著裝載應用程式的 IIS 版本而改變。 Windows Server 2008 (IIS 7.0) 上執行之應用程式的主控件程序識別，是由與應用程式相關聯之應用程式集區的識別來管理。  
  
### <a name="setting-iis-process-identity-for-iis-70-on-windows-server-2008-or-windows-vista"></a>設定 Windows Server 2008 或 Windows Vista 上 IIS 7.0 的 IIS 程序識別  
  
1.  按一下**啟動**，然後**所有程式**，然後按一下**Internet Information Services (IIS) 7 Manager**。  
  
2.  在 [網際網路資訊服務 (IIS) 管理員] 中，展開*\<電腦名稱\>***（使用者帳戶）** 按一下**應用程式集區**。  
  
3.  以滑鼠右鍵按一下應用程式集區，然後按一下**檢視應用程式**以查看應用程式集區相關聯的應用程式。  
  
4.  以滑鼠右鍵按一下應用程式集區，然後按一下**進階設定**顯示應用程式集區的 [進階設定] 對話方塊。  
  
5.  依序按一下省略符號 （...） 按鈕旁的 修改應用程式集區身分識別**識別**下**處理序模型**區段**進階設定**對話方塊方塊。  
  
## <a name="setting-user-access-rights-for-the-iis-server"></a>設定 IIS 伺服器的使用者存取權限  
 程序識別會控管執行中 IIS 應用程式主控件程序可以使用的資訊安全內容，而使用者存取權限則會針對實際存取提供之網頁的帳戶，控制其資訊安全內容。 您必須正確設定這兩種資訊安全內容，才能避免權限錯誤。  
  
 IIS 7.0 支援下列使用者驗證方法：  
  
-   **匿名存取：** 可讓使用者建立匿名連線。 IIS 伺服器會以指定的訪客帳戶來登入使用者。  
  
-   **ASP.NET 模擬**允許應用程式在其中兩個不同內容中執行： 由 IIS 驗證的使用者或您設定的任意帳戶。  
  
-   **基本驗證：** 純文字、 未加密的形式在網路上傳輸密碼。  
  
-   **摘要式驗證：** 只適用於 Active Directory 帳戶，傳送透過網路，而不是純文字密碼的雜湊值。 摘要式驗證可跨 Proxy 伺服器和其他防火牆運作，而且可在「網路分散式撰寫及版本處理」(WebDAV) 目錄上使用。 使用摘要式驗證需要先停用匿名驗證。  
  
-   **表單驗證**Accommodates 高流量網站或公用伺服器上的應用程式的驗證。 表單驗證可讓您管理應用程式層級的用戶端登錄與驗證，而非依賴作業系統提供的驗證機制。  
  
-   **Windows 驗證：** 使用驗證來驗證用戶端連線在 Windows 網域上的。  
  
#### <a name="to-set-user-access-rights-for-a-virtual-directory-in-iis-70"></a>若要在 IIS 7.0 中設定虛擬目錄的使用者存取權限  
  
1.  在 [網際網路資訊服務 (IIS) 管理員] 中，展開*\<電腦名稱\>*，**網站**，和**Default Web Site**中**連線**窗格。  
  
2.  按一下以選取的虛擬目錄，並按一下**功能檢視**底端的工作區窗格中列出的虛擬目錄的可設定功能。  
  
3.  按兩下**驗證**列出虛擬目錄已啟用的驗證方法的工作區 窗格中的功能。  
  
4.  按一下以選取您想要啟用或停用，然後按一下 驗證方法**停用**或**啟用**中**動作**窗格的 IIS 管理員。  
  
    > [!NOTE]
    >  如果**啟用匿名存取**已啟用，IIS 會設定使用者存取權限為已設定匿名使用者識別之前設定的任何其他使用者存取權限啟用驗證方法。  
    >   
    >  若要設定匿名使用者識別，以滑鼠右鍵按一下**匿名驗證**方法，然後按一下**編輯**顯示**編輯匿名驗證認證**對話方塊。  
  
## <a name="general-guidelines-for-resolving-iis-permissions-problems"></a>解決 IIS 權限問題的一般指導方針  
 請依照下列步驟來進行 IIS 權限的疑難排解：  
  
1.  檢查 IIS 伺服器電腦的應用程式記錄中是否記載發生的錯誤。  
  
2.  請依照[IIS 7.0： 設定 IIS 7.0 中的失敗要求追蹤](http://go.microsoft.com/fwlink/?LinkId=130600)疑難排解 IIS 7.0 電腦上的權限問題。  
  
3.  檢查 IIS 伺服器的 IIS 記錄檔是否記載 HTTP 401 錯誤。  
  
     根據預設，在執行 Windows Server 2008 或 Windows Vista 的電腦上，IIS 記錄檔位於下列目錄：  
  
     C:\inetpub\logs\LogFiles\W3SVC1\  
  
    -   如果 IIS 記錄檔的 IIS 7.0 電腦包含 HTTP 401 錯誤，遵循 Microsoft 知識庫文件 943891 中的步驟，「 HTTP 狀態碼 IIS 7.0 中 「 位於[http://support.microsoft.com/kb/943891](http://support.microsoft.com/kb/943891)判斷子狀態碼，並依據狀態碼的權限問題進行疑難排解。  
  
    -   檢查值**cs-username**與 HTTP 401 錯誤相關聯的欄位。 此欄位包含存取 IIS 伺服器的已驗證使用者名稱。 此欄位以連字號 (-) 代表匿名使用者帳戶。 請確定這個帳戶是否擁有適當資源的權限。  
  
4.  確認是否已正確設定 IIS 應用程式主控件程序使用的程序識別認證，以及該帳戶是否擁有適當的權限。 如果用於程序識別的帳戶沒有足夠權限，則請變更帳戶或授與該帳戶適當的權限。  
  
5.  使用中所述的 RegMon 和 FileMon 公用程式[工具和公用程式，以供疑難排解使用](../core/tools-and-utilities-to-use-for-troubleshooting.md)診斷檔案或登錄存取權限問題。  
  
## <a name="see-also"></a>請參閱  
 [疑難排解 BizTalk Server 權限](../core/troubleshooting-biztalk-server-permissions.md)   
 [IIS 7.0： 在 IIS 7.0 中設定驗證](http://go.microsoft.com/fwlink/?LinkId=129909)