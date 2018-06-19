---
title: 安裝 BizTalk Accelerator for RosettaNet (BTARN) 在 BizTalk Server 上 |Microsoft 文件
description: 請參閱硬體和軟體需求、 安裝的步驟和 BTARN BizTalk Server 中的組態步驟
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a40eca3ccd2092cc3024e0ad69d3737bad869180
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22211038"
---
# <a name="install-biztalk-accelerator-for-rosettanet"></a>安裝 BizTalk Accelerator for RosettaNet

## <a name="overview"></a>概觀
安裝 Microsoft BizTalk Accelerator for RosettaNet (BTARN)。
  
> [!NOTE]
>  Enterprise Edition 的 BizTalk Server 上，您可以安裝只有 Enterprise 版的 BizTalk Accelerator for RosettaNet (BTARN)。 在標準版本的 BizTalk 伺服器上，您可以安裝僅標準版的 BizTalk Accelerator for RosettaNet (BTARN)。  
  
 BTARN 安裝包括下列各項：  
  
-   管理 BTARN  
  
-   BizTalk 協調流程設計師 XLANG 排程 (「交易夥伴介面程序」 模式)  
  
-   RosettaNet 實作架構 (RNIF)  
  
-   BTARN 資料庫  
  
-   HTTP 前端 Web 應用程式  
  
## <a name="hardware-and-software-requirements"></a>硬體與軟體需求

最低硬體和軟體需求會與 BizTalk Server 相同。

|  |BizTalk 需求  |SQL 和作業系統需求 |  
|---------|---------|--------- | 
| [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] | [BizTalk Server 2016 的硬體和軟體需求](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) | **SQL Server 硬體和軟體需求**: <br/>[SQL Server 2016](https://msdn.microsoft.com/library/ms143506(v=sql.130).aspx)<br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/><br/>**Windows Server 硬體需求**: <br/>[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/server-basics)<br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx) |
| [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] <br/><br/> BizTalk Server 2013 | [硬體和軟體需求適用於 BizTalk Server 2013 和 2013 R2](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) |**SQL Server 硬體和軟體需求**: <br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/>[SQL Server 2012](https://msdn.microsoft.com/library/ms143506(v=sql.110).aspx)<br/>[SQL Server 2008 R2](https://msdn.microsoft.com/library/ms143506(v=sql.105).aspx)<br/><br/>**Windows Server 硬體需求**: <br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)<br/>[Windows Server 2008 R2](https://technet.microsoft.com/library/dd379511(v=ws.10).aspx)  |

> [!TIP] 
> 列出的硬體需求是最小需求。 每個環境都不同，但您的環境極有可能需要更多需求。 請參閱 [Recommendations for Installing, Sizing, Deploying, and Maintaining a BizTalk Server Solution](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx) (安裝、調整大小、部署和維護 BizTalk Server 解決方案的建議)。 

## <a name="install-and-configure"></a>安裝和設定

### <a name="before-you-begin"></a>開始之前

* BTARN 資料庫中，BTARN 只會設定 SQL Server 的電腦名稱和資料庫名稱屬性。 關於這些屬性的資訊儲存在登錄中。
* 使用成員的帳戶登入 BizTalk Server 系統管理員群組。 
* 在您的 BizTalk Server 下載 BTARN 安裝程式是在`\BizTalk Accelerators`資料夾。
* BizTalk Server，必須先安裝，且必須執行 SQL Server。
* BTARN 和 BizTalk Server 需要 Microsoft.NET Framework 軟體必要元件。 如果您有多個版本的電腦上安裝的.NET Framework，請確定 BtarnAPP Web 應用程式參考傳統.NET Framework 4.0。 您可使用 Internet Information Services (IIS) 管理員設定這個選項。  
* BizTalk 主控件執行個體帳戶和 BizTalk 外掛式主控件執行個體帳戶應該要相同。 否則，BTARN 無法正常運作。  
* BTARN 可讓您將只能個別的服務帳戶並不是群組新增至 BizTalk Server 系統管理員群組或 BizTalk 應用程式使用者群組。  
* 您必須建立 BTSHTTPReceive.dll 的 WebService 延伸模組，設定 IIS 隔離模式。 如需詳細資訊，請參閱 「 疑難排解： 問題與解決方式 」 主題，網址的 「 404 找不到錯誤時，傳送 HTTP 要求 「 項[http://go.microsoft.com/fwlink/?LinkId=188560](http://go.microsoft.com/fwlink/?LinkId=188560)。 此外，請參閱[如何設定 HTTP 接收位置的 IIS](../../core/how-to-configure-iis-for-an-http-receive-location.md)。  
* 加入您的伺服器 (http:// <*伺服器名稱*>) 至 Internet Explorer 安全性選項的本機網際網路區域。  
*  如果用來設定 BTARN 的遠端 SQL 執行個體使用非預設連接埠，則 SQL Server 用戶端工具必須安裝在本機。 如需詳細資訊，請參閱[多重電腦環境中的 BizTalk Server 安裝指南 》](../../install-and-config-guides/install-biztalk-server-in-a-multi-computer-environment.md)。
*  不同的群組必須用於 BizTalk Server 的組態期間，角色-BizTalk 系統管理員、 BizTalk 主控件使用者 」 和 BizTalk 外掛式主控件使用者。  
*  BTARN 不支援設定 BTARN 資料庫的 SQL 執行個體別名的使用。  

### <a name="install-btarn"></a>安裝 BTARN

1.  執行 BTARN **setup.exe**以系統管理員身分。
  
2.  選取 [安裝]。  
  
3.  在**客戶資訊**頁面上，輸入您的使用者名稱、 組織及產品金鑰，然後按**下一步**。  
  
4.  在**合約**頁面上，閱讀使用者授權合約，然後按**接受**。  
  
    > [!NOTE]
    >  如果您不接受授權合約，您不能繼續安裝。  
  
5.  在**安裝選項**頁面上，選取**完成**完整安裝或**自訂**進行部分安裝。 請確定安裝路徑是正確的，然後按一下 **下一步**。  
  
    > [!NOTE]
    >  如果您選取**自訂**，選取要從安裝的元件**自訂安裝**頁面。 如果您選擇安裝 SDK 或文件集元件，您必須再執行安裝程式安裝.NET Framework。  
  
6.  在**摘要**頁面上，檢閱您要安裝，然後再按一下元件**安裝**。 **安裝進度**螢幕顯示的安裝程序的進度。  
  
7.  在**安裝完成**頁面上，確定**執行組態精靈**中已選取，然後按一下**完成**。  
  
     [BTARN 組態精靈] 隨即開啟。 接下來，您會設定 BTARN。  
  
    > [!IMPORTANT]
    >  如果您執行只安裝 BTARN HTTP 前端功能的自訂安裝，BTARN 組態可能會失敗之後安裝程式已完成，顯示 「 無法建立功能的物件： WebApp 」 錯誤。 如果發生這種情況，將兩個檔案複製 (**Microsoft.VC80.ATL.manifest**和**atl80.dll**) 從 BizTalk Server 的電腦上安裝，若要安裝 BTARN HTTP 前端功能的電腦。  
    >   
    >  如果與 BizTalk Server 在相同電腦上安裝 Visual Studio，兩個檔案的來源資料夾是 *< 磁碟機\>*: \Program Files\Microsoft Visual Studio 11.0\VC\redist\x86\Microsoft.VC100.ATL。 如果 BizTalk server 上未安裝 Visual Studio，BizTalk server 上的兩個檔案的來源資料夾是資料夾之下的 *< 磁碟機\>*: \WINDOWS\WinSxS。 檔案版本應為 8.0.50727.42。 在已安裝 HTTP 前端功能的電腦上目的地資料夾是 BTARN 安裝目錄 (根據預設， *< 磁碟機\>*: \Program Files\Microsoft BTARN)。  
    >   
    >  您將這些檔案複製到電腦已安裝 HTTP 前端功能之後，重新執行**Configuration.exe**。  
  
### <a name="configure-btarn"></a>設定 BTARN  

> [!TIP]
 >  之前設定 BTARN，請確定您將對應的.NET Framework 在 IIS 中的處理常式對應底下。 此外，當設定 BTARN，您可能需要手動建立 IIS_WPG 群組。  
   
1.  在**Microsoft BTARN 組態精靈**頁面上，選取**基本組態**設定伺服器預設設定，或**自訂組態**至設定伺服器使用進階的組態選項。  
  
    > [!NOTE]
    >  如果您想要設定 BTARN 使用本機系統管理員帳戶，請輸入帳戶做為 *< 機器名稱\>\\< 系統管理員名稱\>* 中**使用者識別碼**欄位**服務認證**區域。  
  
2.  在**資料庫伺服器名稱**文字方塊中，確認顯示的伺服器名稱正確無誤。 在**服務認證**區域中，輸入執行服務的帳戶 （及網域） 的使用者名稱和密碼。 按一下**設定**。  
  
3.  如果您的帳戶具有系統管理權限，請按一下**是**以便進行設定。  
  
4.  如果您選取**基本組態**在步驟 1 中，確認要在中設定的元件清單**摘要**對話方塊，然後按一下**下一步**。 移至步驟 10。  
  
5.  如果您選取**自訂組態**在步驟 1 中，執行下列步驟：  
  
    > [!NOTE]
    >  如果您在任何 BTARN 資料庫的名稱中使用特殊字元，BTARN 組態將會失敗。  
  
6.  在 設定執行階段， **Microsoft BTRAN 組態**對話方塊中，按一下 **執行階段**的左窗格中。 在右邊**執行階段**] 窗格中，按一下 [**啟用這部電腦上的執行階段功能**。 若要加入現有的資料庫群組，請清除**您想要建立新的資料庫群組**。 請選取適當的 Web 伺服器名稱、連接埠編號、資料存放區、應用程式集區服務帳戶以及 BizTalk HTTP 接收虛擬資料夾。  
  
7.  若要設定 WebApps 功能，在**Microsoft BTRAN 組態**對話方塊中，按一下  **WebApps**在左的窗格中，然後按一下**啟用這部電腦上的執行階段功能**. 輸入適當的 BizTalk Server 名稱和連接埠號碼，或選取的預設值。 選取適當的 Web 應用程式虛擬資料夾。  
  
8.  按一下 [套用組態]。  
  
9. 在**摘要**頁面上，按一下**下一步**。  
  
10. 在**完成設定**頁面上，按一下**完成**。  
  
    > [!NOTE]
    >  在您安裝 BTARN 之後，您的系統管理員必須將使用者加入至 BAS「商務使用者」、「商務經理人」和「商務管理員」群組。 如果您是系統管理員，則需要填入這些群組並登出，然後登入，以將您自己新增至群組。
  
    > [!WARNING]
    >  BizTalk 系統管理員、 BizTalk 主控件使用者 」 和 BizTalk 外掛式主控件使用者設定 BizTalk Server 時，必須使用三個不同的群組。  

## <a name="start-the-artifacts"></a>啟動成品
BTARN 協調流程傳送埠和接收位置不會自動啟動設定 BTARN 之後。
  
> [!NOTE]
>  您必須先啟動 PrivateInitiator_To_LOB 傳送埠和 PrivateResponder_To_LOB 傳送埠，然後才能啟動 PrivateInitiatorProcess 和 PrivateResponderProcess 協調流程。  
  
-   在已將 Internet Information Services (IIS) 虛擬伺服器設定為使用安全通訊端層 (SSL) 的電腦中，您必須將虛擬伺服器設定為可接受用戶端憑證。 請參閱[步驟 4： 啟用安全通訊端在 IIS 中的層](step-4-enabling-secure-sockets-layer-in-iis.md)中[按兩下動作 」 教學課程](double-action-tutorial.md)。
  
 
1.  開啟**BizTalk Server 管理**身為系統管理員。  
  
2.  展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk Application 1**。  
  
3.  按一下**傳送埠**。 在右窗格中，每一個未啟動的傳送埠，以滑鼠右鍵按一下，然後按一下 **啟動**。  
  
4.  按一下**接收埠**和**接收位置**。 在右窗格中，為每個接收位置未啟動，以滑鼠右鍵按一下，然後按一下**啟動**。  
  
    > [!NOTE]
    >  您必須啟動 PrivateInitiator_To_LOB 傳送埠和 PrivateResponder_To_LOB 傳送埠，然後才能啟動 PrivateInitiatorProcess 和 PrivateResponderProcess 協調流程。  
  
5.  按一下**協調流程**和**接收位置**。 在右窗格中，每個協調流程未啟動，以滑鼠右鍵按一下，然後按一下 **啟動**。  
  
## <a name="restart-your-computer"></a>重新啟動電腦  
  
重新啟動您的電腦，以套用對組態和權限進行的任何修改。  
  
> [!NOTE]
>  開發人員可以選擇在單一伺服器上安裝和設定 BTARN 以進行開發、執行或測試動作。 開發人員使用這個伺服器在將其移動至生產線之前，寫入他們自訂的節點並加以測試。  
  
 如需在單一伺服器上安裝 BTARN 的詳細資訊，請參閱[回送教學課程](loopback-tutorial.md)。
  
## <a name="next-steps"></a>後續的步驟  
  
* [升級 RosettaNet 加速器](upgrade-biztalk-accelerator-for-rosettanet.md)
* [解除安裝 RosettaNet 加速器](uninstall-biztalk-accelerator-for-rosettanet.md)
* [安裝的疑難排解，並查看已知的安裝問題](troubleshoot-known-issues-installation.md)