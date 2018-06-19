---
title: 附錄 d： 建立 SMTP 伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7441ba9-a498-42ec-a04d-7f2731407373
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f4d4acc35f5cb38be5f783ee7c4017c8ada83e2
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22300134"
---
# <a name="appendix-d-create-the-smtp-server"></a>附錄 D︰建立 SMTP 伺服器
建立 SQL Server Database Mail 所使用的 SMTP 伺服器。  
  
使用下列任何 SQL 版本，需要有 SQL Server Database Mail 才能設定 BAM 警示： 

* [!INCLUDE[sqlserver2016_md](../includes/sqlserver2016-md.md)]
* [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)]
* [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] 
  
 SQL Server Database Mail 使用 SMTP 伺服器傳送 BAM 警示。 SMTP 伺服器隨附於網際網路資訊服務 (IIS)。 SMTP 可以安裝在本機 BizTalk Server 上，或安裝在已安裝 IIS 的另一部伺服器上。  
  
> [!IMPORTANT]
>  一般而言，用戶端作業系統 (例如 Windows 10、Windows 7 等) 都不包含 SMTP 伺服器功能。 您可以在 IIS 內使用 [SMTP 電子郵件] 功能，連接至 Windows Server 上的現有 SMTP 伺服器。 [SMTP 電子郵件] 功能不是 SQL Server Database Mail 所需的 SMTP 伺服器。 因此，本主題不包含在用戶端作業系統上安裝和設定 SMTP 伺服器的步驟。  

## <a name="install-and-configure-the-smtp-server"></a>安裝和設定 SMTP 伺服器  
  
這些步驟適用於：

* Windows Server 2016
* Windows Server 2012 R2
* Windows Server 2012
  
### <a name="install-smtp-server"></a>安裝 SMTP 伺服器  
   
1.  在 [伺服器管理員] 中，選取左窗格中的 [儀表板]。  
  
3.  選取 [新增角色及功能]。 您也可以從右上角的 [管理] 功能表開啟 [新增角色及功能]。  
  
4.  在 [開始之前]中，選取 [下一步]。  
  
5.  選取 [角色型或功能型安裝]，然後選取 [下一步]。  
  
6.  選取 [從伺服器集區選取伺服器]，並選取所需的伺服器，然後選取 [下一步]。 [伺服器選取項目] 視窗會列出已使用 [伺服器管理員] 中的 [新增伺服器] 所新增的伺服器。 根據預設，它會選取本機伺服器。  
  
7.  在 [伺服器角色] 中，選取 [下一步]。  
  
8.  在 [功能] 中，核取 [SMTP 伺服器]。 系統出現提示時，請選取 [新增功能]。 選取 [下一步]。  
  
9. 在 [確認] 中，選取 [必要時自動重新啟動目的地伺服器]，然後選取 [安裝]。 完成後，請選取 [關閉]。  

### <a name="configure-the-smtp-server"></a>設定 SMTP 伺服器  
 下列步驟使用 IIS 6.0 管理員來設定 SMTP 虛擬伺服器︰  
  
1.  開啟 IIS 管理員︰在 [開始] 中，搜尋 **inetmgr6.exe**，並開啟它。  
  
2.  展開電腦名稱。 以滑鼠右鍵按一下 [SMTP 虛擬伺服器 #1]，然後選取 [內容]。  
  
3.  在 [存取] 索引標籤中，選取 [轉送] 按鈕。  
  
4.  選取 [新增]。 在 [單一電腦] 中，輸入 `127.0.0.1`，然後選取 [確定]。  
  
     新增 127.0.0.1，即允許本機伺服器傳送來自這個 SMTP 伺服器的訊息。 如果您想要其他電腦傳送來自這個 SMTP 伺服器的訊息，請輸入其 IP 位址。  
  
5.  在 [傳遞] 索引標籤中，選取 [輸出安全性]。 選擇下列項目：  
  
     **匿名存取**︰不需要帳戶名稱或密碼。 這個選項會停用 SMTP 伺服器的驗證。  
  
     **基本驗證**︰您要連接之伺服器的帳戶名稱和密碼會以純文字傳送。 您輸入的這個帳戶會傳輸電子郵件。 將電子郵件傳送至個人帳戶或 Exchange 帳戶時，可以選取基本驗證。 因為這些認證會以純文字傳遞，所以建議啟用 **TLS 加密**。  
  
     **整合式 Windows 驗證**：使用 Windows 網域帳戶名稱和密碼進行驗證。 您輸入的帳戶會傳輸電子郵件。  
  
     **TLS 加密**：與 SSL 類似，TLS 會保護連接安全。 需要在這部伺服器上安裝有效的 SSL 伺服器憑證。  
  
    > [!TIP]
    >  若要使用個人電子郵件帳戶來測試核心 SMTP 功能 (包含 Exchange 帳戶)，請選取 [匿名存取]。 選取 [基本驗證] 時，SMTP 會使用 AUTH 命令。 某些電子郵件提供者可能會因 AUTH 命令而失敗。 如果 AUTH 命令失敗，可能會在 SMTP 伺服器的 Windows 事件記錄檔中記錄錯誤。  
  
6.  在 [傳遞] 索引標籤中，選取 [輸出連線]。 TCP 通訊埠預設為 25。 如果您在防火牆內開啟不同的通訊埠，則可以輸入該連接埠。 選取 [確定]。  
  
7.  在 [傳遞] 索引標籤中，選取 [進階]。 預設會列出本機伺服器的 [完整網域名稱]。 根據網際網路提供者，[智慧主機] 屬性可以空白。 您可能需要連絡網際網路提供者，確認是否需要智慧主機。 否則，您可以輸入 smtp.*EMailProvider*.com。  
  
    > [!NOTE]
    >  「智慧主機」 (也稱為轉送主機) 是 Exchange 伺服器用來路由傳送所有外寄訊息的專用伺服器。 「智慧主機」接收到訊息時，「智慧主機」會將訊息轉送至遠端網域。 「智慧主機」的目的是要改善 Exchange Server 的效能。 Exchange Server 只會傳輸至智慧主機；而不是重複連絡遠端網域直到建立連線。  
  
8.  選取 [確定] 關閉所有視窗。  
  
9. 重新啟動 SMTP 伺服器︰ 以滑鼠右鍵按一下 [SMTP 虛擬伺服器 #1]，並選取 [停止]，然後選取 [啟動]。 需要重新啟動，才能套用 SMTP 伺服器設定。 

  
## <a name="windows-server-2008-r2-install-and-configure-smtp-server"></a>Windows Server 2008 R2：安裝和設定 SMTP 伺服器  
  
### <a name="install-smtp-server"></a>安裝 SMTP 伺服器  
 下列步驟會安裝 SMTP 伺服器功能︰  
  
1.  在 [伺服器管理員] 中，選取 [功能]，然後選取 [新增功能]。  
  
3.  在 [新增功能] 中，選取 [SMTP 伺服器]。 系統出現提示，請選取 [新增所需的角色服務]，然後選取 [下一步]。  
  
4.  選取 [下一步]，以繼續進行安裝。  
  
5.  在 [確認安裝選項] 視窗中，選取 [安裝]。 完成後，請選取 [關閉]。  
  
### <a name="configure-the-smtp-server"></a>設定 SMTP 伺服器  
 下列步驟使用 IIS 6.0 管理員來設定 SMTP 虛擬伺服器︰  
  
1.  開啟 IIS 6.0 管理員：在 [開始] 中，搜尋 **IIS**，然後選取 [網際網路資訊服務 (IIS) 6.0 管理員]。  
  
2.  展開電腦名稱。 以滑鼠右鍵按一下 [SMTP 虛擬伺服器 #1]，然後選取 [內容]。  
  
3.  在 [存取] 索引標籤中，選取 [轉送] 按鈕。  
  
4.  選取 [新增]。 在 [單一電腦] 中，輸入 `127.0.0.1`，然後選取 [確定]。  
  
     新增 127.0.0.1，即允許本機伺服器傳送來自這個 SMTP 伺服器的訊息。 如果您想要其他電腦傳送來自這個 SMTP 伺服器的訊息，請輸入其 IP 位址。  
  
5.  在 [傳遞] 索引標籤中，選取 [輸出安全性]。 選擇下列項目：  
  
     **匿名存取**︰不需要帳戶名稱或密碼。 這個選項會停用 SMTP 伺服器的驗證。  
  
     **基本驗證**︰您要連接之伺服器的帳戶名稱和密碼會以純文字傳送。 將電子郵件傳送至個人帳戶或 Exchange 帳戶時，可以選取基本驗證。 因為這些認證會以純文字傳遞，所以建議啟用 **TLS 加密**。  
  
     **整合式 Windows 驗證**：使用 Windows 網域帳戶名稱和密碼進行驗證。 您輸入的帳戶會傳輸電子郵件。  
  
     **TLS 加密**：與 SSL 類似，TLS 會保護連接安全。 需要在這部伺服器上安裝有效的 SSL 伺服器憑證。  
  
    > [!TIP]
    >  若要使用個人電子郵件帳戶來測試核心 SMTP 功能 (包含 Exchange 帳戶)，請選取 [匿名存取]。 選取 [基本驗證] 時，SMTP 會使用 AUTH 命令。 某些電子郵件提供者可能會因 AUTH 命令而失敗。 如果 AUTH 命令失敗，可能會在 SMTP 伺服器的 Windows 事件記錄檔中記錄錯誤。  
  
6.  在 [傳遞] 索引標籤中，選取 [輸出連線]。 TCP 通訊埠預設為 25。 如果您在防火牆內開啟不同的通訊埠，則可以輸入該連接埠。 選取 [確定]。  
  
    > [!TIP]
    >  TCP 通訊埠可以用於傳入連接和傳出連接。  
  
7.  在 [傳遞] 索引標籤中，選取 [進階]。 預設會列出本機伺服器的 [完整網域名稱]。 根據網際網路提供者，[智慧主機] 屬性可以空白。 您可能需要連絡網際網路提供者，確認是否需要智慧主機。 否則，您可以輸入 smtp.*EMailProvider*.com。  
  
    > [!NOTE]
    >  「智慧主機」 (也稱為轉送主機) 是 Exchange 伺服器用來路由傳送所有外寄訊息的專用伺服器。 「智慧主機」接收到訊息時，「智慧主機」會將訊息轉送至遠端網域。 「智慧主機」的目的是要改善 Exchange Server 的效能。 Exchange Server 只會傳輸至智慧主機；而不是重複連絡遠端網域直到建立連線。  
  
8.  選取 [確定] 關閉所有視窗。  
  
9. 需要重新啟動，才能套用 SMTP 伺服器設定。 重新啟動 SMTP 伺服器︰ 以滑鼠右鍵按一下 [SMTP 虛擬伺服器 #1]，並選取 [停止]，然後選取 [啟動]。  
  
  
## <a name="test-the-smtp-server"></a>測試 SMTP 伺服器  
 Telnet 可以用來測試 SMTP 伺服器組態。 下列步驟使用您設定的 SMTP 伺服器將訊息傳送至電子郵件地址。 [http://support.microsoft.com/kb/153119](http://support.microsoft.com/kb/153119) 提供的 telnet 命令的描述。  
  
1.  以系統管理員身分開啟命令視窗。
  
2.  在命令提示字元中，輸入：  
  
     `telnet localhost 25`  
  
     如果未安裝 telnet，請輸入下列命令進行安裝︰  
  
     `pkgmgr /iu:"TelnetClient"`  
  
3.  輸入下列命令開始通訊︰  
  
     `EHLO server`  
  
4.  輸入郵件寄件者地址︰  
  
     `MAIL FROM: *YourEmailAddress*@*YourProvider*.com`  
  
     例如，輸入：  
  
     `MAIL FROM: EmailAddress@outlook.com`  
  
5.  輸入郵件收件者地址︰  
  
     `RCPT TO: *YourEmailAddress*@*YourProvider*.com`  
  
     例如，輸入：  
  
     `RCPT TO: EmailAddress@outlook.com`  
  
6.  輸入下列命令，告知準備好要傳送資料的 SMTP 伺服器︰  
  
     `DATA`  
  
7.  輸入下列命令，輸入主旨︰  
  
     `Subject: Test Message`  
  
8.  按 Enter 兩次。  
  
9. 輸入下列命令，輸入訊息主體：  
  
     `This is the message body of the test message.`  
  
10. 按 Enter，並輸入句號 (.)，然後按 Enter。  
  
 檢查電子郵件訊息的 RCPT TO 位址。 如果未傳遞電子郵件 (請檢查您的收件匣和垃圾郵件資料夾)，則不會成功傳送訊息，而訊息可能位在 SMTP Queue 資料夾 (C:\inetpub\mailroot\Queue) 中。  
  