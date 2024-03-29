---
title: 疑難排解和已知的問題與 BizTalk RosettaNet Accelerator (BTARN) 在 BizTalk 伺服器上安裝 |Microsoft Docs 」
description: 安裝 BTARN 安裝在 BizTalk Server 中的 SQL、 主控件執行個體，與已知的錯誤的服務帳戶建議
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c169a0871826aaaae9341f3ccafcb3e888ffbdbb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974623"
---
# <a name="troubleshoot-the-installation-and-see-the-known-install-issues"></a>疑難排解安裝問題，並查看已知的安裝問題


## <a name="do-not-install-sql-server-on-the-domain-controller-computer"></a>請勿在網域控制站電腦上安裝 SQL Server  
 如果您在相同的電腦，您的網域控制站電腦上安裝 SQL Server，它會嘗試建立 SQL 傳送埠時傳回下列錯誤訊息：  

```
Error: Failed updating binding information.  
BindingException: Could not validate TransportTypeData or Address properties for Primary Transport of Send Port 'SendPort1'. Exception from HRESULT: 0x80131500.  
Error: Failed updating binding information.  
BindingException: Could not validate TransportTypeData or Address properties for Primary Transport of Send Port 'SendPort1'. Exception from HRESULT: 0x80131500  
```

> [!IMPORTANT]
>  請勿在網域控制站電腦上安裝 SQL Server。  

## <a name="service-account-for-the-application-pools-must-be-the-same-as-the-service-account-for-the-isolated-host-and-host-instances"></a>應用程式集區的服務帳戶必須和外掛式主控件和主控件執行個體的服務帳戶相同。  
 如果設定 BTARN 應用程式集區的服務帳戶與外掛式主控件帳戶不同，BTARN 不會正確處理內送訊息。 當接收.aspx 頁面呼叫管線時，管線中沒有適當的憑證的存取權。 因此，它不會解密內送訊息或驗證簽章。 此外，它將無法存取 MessageBox 資料庫。  


## <a name="known-install-issues"></a>已知的安裝問題


### <a name="btarn-http-front-end-feature-configuration-fails"></a>BTARN HTTP 前端功能組態失敗  
 **問題**  

 如果您執行只安裝 BTARN HTTP 前端功能的自訂安裝，BTARN 組態可能會失敗，發生下列錯誤，安裝程式完成之後： 

`Failed to create object for feature: WebApp`  

 **解決方式**  

手動複製檔案，並重新設定： 

1. 從 BizTalk Server 電腦的下列兩個檔案複製到您安裝 BTARN HTTP 前端功能的電腦中：

   - Microsoft.VC80.ATL.manifest  

   - atl80.dll  

     如果在 BizTalk Server 的同一部電腦上安裝 Visual Studio，兩個檔案的來源資料夾是 <*磁碟機*>: \Program Files\Microsoft Visual Studio < 版本\>\VC\redist\x86\Microsoft.VC100.ATL.  

     如果在相同的 BizTalk Server 電腦上未安裝 Visual Studio，兩個檔案的來源資料夾是在 <*磁碟機*>: \WINDOWS\WinSxS。  

2. 將複製的檔案新增到您安裝 BTARN HTTP 前端功能的電腦上。 根據預設，將檔案複製到 <*磁碟機*>: \Program Files\Microsoft BizTalk Accelerator for RosettaNet。  

3. 您將檔案複製到 HTTP 前端電腦之後，請執行**Configuration.exe**一次。  

### <a name="some-btarn-assemblies-stay-in-gac-after-uninstalling"></a>部分 BTARN 組件保持在 GAC 中解除安裝之後  
 **問題**  

 當您解除安裝 BTARN 時，某些組件仍保留在全域組件快取 (GAC) 中。  

 **解決方式**  

 先從 GAC 移除組件，再重新安裝 BTARN。  

 使用**BtarnClean**公用程式 」 從 SDK 移除組件。 公用程式會執行下列動作：  

- 停止和取消登錄所有的 BTARN 協調流程。  

- 停止和刪除所有關聯的連接埠。  

- 解除部署所有的 Microsoft.Solutions.BTARN.* 組件。  

  執行公用程式後，如果 GAC 中仍存在組件，請開啟 [檔案總管]，移至 "C:\Windows\Assembly" 資料夾，手動刪除所有開頭為 Microsoft.Solutions.BTARN 的組件。  

### <a name="service-unavailable-error-on-64-bit-os"></a>64 位元作業系統上的服務無法使用錯誤
 **問題**  

 您可能會收到`Service Unavailable`錯誤時嘗試存取 BTARN HTTP 接收位置在 64 位元 Windows 作業系統上的。  

 **原因**  

 這個問題可能是由 "RPCProxy.dll" ISAPI 篩選器所造成。  

 **解決方式**  

移除 RPC proxy ISAPI 篩選器的參考，然後重新啟動 IIS:

1.  在 [Internet Information Services (IIS) 管理員] 中，以滑鼠右鍵按一下**Web Sites**，然後按一下**屬性**。  

2.  在 [**的網站內容**] 對話方塊中，按一下**ISAPI 篩選器**索引標籤上，移除**RPC Proxy**篩選，然後按一下 **[確定]**。  

3.  重新啟動 IIS。  

4.  在您重新啟動 IIS 之後，嘗試存取 http://localhost 。 您應該會從網際網路瀏覽器收到 400 訊息。  

### <a name="sql-server-mixed-mode-not-supported"></a>不支援的 SQL Server 混合模式  
BTARN 不支援混合模式中的 SQL Server。  

### <a name="run-setupx64bat-to-set-up-the-double-action-pipautomation-orchestration-sample"></a>執行 setupx64.bat，以設定雙向動作 PIPAutomation 協調流程範例 

執行中的 setupx64.bat \Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction 資料夾設定雙向動作 PIPAutomation 協調流程範例。

### <a name="download-the-btarn-setup-file-from-the-web-to-a-temp-folder"></a>將 BTARN 安裝程式檔案從 Web 下載到 Temp 資料夾  
 **問題**  

 如果您下載 BTARN 自動解壓縮可執行檔從 Web，並將它儲存到 BizTalk Server 的根資料夾中，當您嘗試執行的可執行檔中，而 BizTalk**安裝精靈**執行，而不是 BTARN 安裝精靈。  

 **解決方式**  

 下載 BTARN 自動解壓縮可執行檔，並將檔案儲存到暫存資料夾。
