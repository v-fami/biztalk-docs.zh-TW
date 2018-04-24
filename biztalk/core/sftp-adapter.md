---
title: SFTP 配接器 |Microsoft 文件
description: 建立或設定接收位置和傳送埠使用 SFTP 配接器在 BizTalk Server 中，包括使用 SFTP 配接器的常見問題集
ms.custom: ''
ms.date: 02/26/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f64c4c8-64a0-4e43-9660-b5c2d75d28aa
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d28c3b453ab3e704ddbb06ed42b23dc641a6711
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="sftp-adapter"></a>SFTP 配接器
BizTalk Server 包含 **SFTP** 配接器傳送和接收訊息的安全 FTP 伺服器，使用 SSH 檔案傳輸通訊協定。 本主題包含設定的步驟 **SFTP** 接收位置，並設定 SFTP 傳送埠來接收和傳送訊息從安全 FTP 伺服器。 它也包含常見的問題和答案。

## <a name="prerequisites"></a>필수 구성 요소
**從 BizTalk Server 2016 開始**，SFTP 配接器用來連接 SFTP 的 WinSCP，因此可支援較大範圍的 SFTP 伺服器。 **下載[WinSCP](http://winscp.net)** 對 BizTalk Server 執行階段。 請務必支援的 WinSCP 版本簽入[硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)

BizTalk Server 2013 R2 和先前的版本不支援 WinSCP。
  
## <a name="configure-the-receive-location"></a>設定接收位置
  
> [!NOTE]
>  之前建立的接收位置，您必須已經新增單向接收埠。 請參閱[建立接收埠](../core/how-to-create-a-receive-port.md)如需特定步驟。  
  
 
1.  在 BizTalk Server 管理主控台中，展開 BizTalk Server 中，展開**BizTalk 群組**，依序展開**應用程式**，然後展開 應用程式在您要建立接收位置。  
  
2.  在左窗格中按一下 **[接收埠]** 節點，在右窗格中以滑鼠右鍵按一下您想與新接收位置建立關聯的接收埠，然後按一下 **[屬性]**。  
  
3.  在左窗格中 **接收埠屬性** 對話方塊中，選取 **接收位置**, ，並在右窗格中按一下 **新增** 來建立新的接收位置。  
  
4.  在 **接收位置屬性** 對話方塊中，於 **傳輸** 區段中，選取 **SFTP** 從 **類型** 下拉式清單，然後按一下 **設定** 設定接收位置的傳輸屬性。  
  
5.  在 **SFTP 傳輸屬性**, ，執行下列動作︰  
 
     **其他人**
         
    |使用|動作|  
    |--------------|----------------|  
    |連接限制|指定伺服器最多可以開啟的並行連線數目。<br /><br /> 此設定是每一部伺服器，而且每個接收位置。 請考慮下列案例：<br /><br /> -有兩個接收位置具有相同的組態屬性值，包括 ConnectionLimit 屬性設定為相同的值。 例如，屬性是設定為 6。 在此情況下，沒有一個連接集區 （6 可用的連線），同時適用於接收位置。<br /><br /> -有兩個接收位置設定為相同的設定值，而且可 ConnectionLimit 屬性設定為不同的值。 例如，ReceiveLocation1 屬性設定為 6，ReceiveLocation2 屬性設定為 5。 在此情況下，每個接收位置有自己的連接集區與它自己的可用連線。 ReceiveLocation1 連接集區具有 6 可用的連線。 ReceiveLocation2 連接集區具有 5 個可用的連線。|  
    |Log | 適用於從 BizTalk Server 2016 開始。 <br/><br/>輸入建立用戶端記錄檔的完整路徑。 您可以使用此記錄檔來解決所有錯誤。|
  
     **輪詢**  
  
    |使用|動作|  
    |--------------|----------------|  
    |輪詢間隔|指定配接器會輪詢伺服器的間隔。 若要連續輪詢，請將此值設為零。<br /><br /> **預設值︰** 5|  
    |單位|指定用於指定輪詢間隔的單位，例如：秒、分鐘、小時或天。<br /><br /> **預設值︰** 秒|  
  
     **Proxy** （可以使用開頭為 BizTalk Server 2013 R2）  
  
    |使用|動作|  
    |--------------|----------------|  
    |位址|指定 Proxy 伺服器的 DNS 名稱或 IP 位址。|  
    |密碼|指定 Proxy 伺服器的密碼。|  
    |通訊埠|指定 Proxy 伺服器的連接埠。|  
    |型別|指定 Proxy 伺服器使用的通訊協定。|  
    |UserName|指定 Proxy 伺服器的使用者名稱。|  
  
     **安全性**  
  
    |使用|動作|  
    |--------------|----------------|  
    |接受任何 SSH 伺服器主機金鑰|當 **True**, ，接收位置會接受來自伺服器的所有 SSH 公開主機金鑰。 當 **False**, ，接收位置使用的伺服器指紋進行驗證。 您輸入在指紋 **[sshserverhostkeyfingerprint]** 屬性。<br /><br /> **預設值︰** False|  
    |用戶端驗證模式|選取接收位置會使用來驗證用戶端到 SSH 伺服器的驗證方法。 如果設定為 **密碼**, ，您必須輸入中的值 **密碼** 屬性。 如果設定為 **PublicKeyAuthentication**, ，您必須輸入使用者的私密金鑰 **私密金鑰** 屬性。 如果設定為 **MultiFactorAuthentication** 必須輸入 **Username** 與其 **密碼** 和 **PrivateKey**。 此外，如果密碼保護私密金鑰，輸入的密碼也 **PrivateKeyPassword** 屬性。<br /><br /> **預設值︰** 密碼|  
    |加密編碼器 |適用於從 BizTalk Server 2013 R2。 <br/><br/>輸入加密密碼的類型。<br/><br/>BizTalk Server 2013 R2 選項： 自動、 AES、 和 TripleDES<br/><br/>BizTalk Server 2016 選項： 自動、 AES、 Arcfour、 Blowfish、 TripleDES、 和 DES|  
    |密碼|如果您將設定指定 SFTP 使用者密碼 **ClientAuthenticationMode** 至 **密碼**。|  
    |私密金鑰|如果您設定，請指定 SFTP 使用者的私密金鑰 **ClientAuthenticationMode** 至 **PublicKeyAuthentication**。<br /><br /> **注意︰** 私密金鑰檔案必須是指定的.ppk 檔案。|  
    |私密金鑰密碼|如果要求中指定索引鍵，指定私密金鑰密碼， **PrivateKey** 屬性。|  
    |SSH 伺服器主機金鑰指紋|指定 SSH 伺服器的公開主機金鑰指紋。|  
    |使用者名稱|指定 SFTP 伺服器登入的使用者名稱。|  
  
     **SSH 伺服器**  
  
    |使用|動作|  
    |--------------|----------------|  
    |檔案遮罩|指定從安全 FTP 伺服器擷取檔案時要使用的檔案遮罩。|  
    |資料夾路徑|指定在安全 FTP 伺服器上接收位置可以擷取檔案的資料夾路徑。|  
    |通訊埠|指定進行檔案傳輸的安全 FTP 伺服器上的連接埠位址。|  
    |伺服器位址|指定安全 FTP 伺服器的伺服器名稱或 IP 位址。|  
  
6.  按一下 **[確定]**。  
  
7.  在 **[接收位置屬性]** 對話方塊中輸入適當的值，以完成接收位置的組態，然後按一下 **[確定]** 儲存設定值。 如需有關資訊**接收位置屬性**對話方塊中，請參閱[建立接收位置](../core/how-to-create-a-receive-location.md)。
 
## <a name="configure-the-send-port"></a>設定傳送埠  
  
1.  在 BizTalk Server 管理主控台中，建立新的傳送埠，或按兩下現有的傳送埠進行修改。 如需詳細資訊，請參閱[建立傳送埠](../core/how-to-create-a-send-port2.md)。 設定所有傳送埠選項，並指定 **SFTP** 的 **類型** 選項 **傳輸** 區段 **一般**  索引標籤。  
  
2.  在 **一般** 索引標籤的 **傳輸** 區段中，按一下 **設定**  按鈕。  
  
3.  在 **SFTP 傳輸屬性**, ，輸入下列命令︰  
  
    **其他人**
    
    |使用|動作|  
    |--------------|----------------|  
    |連接限制|指定伺服器最多可以開啟的並行連線數目。|  
    |Log | 適用於從 BizTalk Server 2016 開始。 <br/><br/>輸入建立用戶端記錄檔的完整路徑。 您可以使用此記錄檔來解決所有錯誤。|
    |暫存資料夾 | 適用於從 BizTalk Server 2013 R2。 <br/><br/>在能夠自動移到相同伺服器上的必須位置前，會將大型檔案上傳到 SFTP 伺服器中的暫時資料夾|  
    
    **Proxy** （可從 BizTalk Server 2013 R2）
    
    |使用|動作|  
    |--------------|----------------|  
    |位址|指定 Proxy 伺服器的 DNS 名稱或 IP 位址。|  
    |密碼|指定 Proxy 伺服器的密碼。|  
    |通訊埠|指定 Proxy 伺服器的連接埠。|  
    |型別|指定 Proxy 伺服器使用的通訊協定。|  
    |使用者名稱|指定 Proxy 伺服器的使用者名稱。|  
    
    **安全性**
    
    |使用|動作|  
    |--------------|----------------|  
    |存取任何 SSH 伺服器主機金鑰|當 **True**, ，傳送埠會接受來自伺服器的所有 SSH 公開主機金鑰。 當 **False**, ，連接埠符合主索引鍵與指定之索引鍵 **SSHServerHostKey** 屬性。<br /><br /> **預設值︰** False|  
    |用戶端驗證模式|指定傳送埠用於向 SSH Server 驗證用戶端的驗證方法。 如果設定為 **密碼**, ，您必須輸入中的值 **密碼** 屬性。 如果設定為 **PublicKeyAuthentication**, ，您必須輸入使用者的私密金鑰 **私密金鑰** 屬性。 如果設定為 **MultiFactorAuthentication** 必須提供 **Username** 使用其 **密碼** 和 **PrivateKey**。 此外，如果密碼保護私密金鑰，輸入的密碼也 **PrivateKeyPassword** 屬性。<br /><br /> **預設值︰** 密碼|  
    |加密編碼器 | 適用於從 BizTalk Server 2013 R2。<br/><br/>輸入加密密碼的類型。<br/><br/>BizTalk Server 2013 R2 選項： 自動、 AES、 和 TripleDES<br/><br/>BizTalk Server 2016 選項： 自動、 AES、 Arcfour、 Blowfish、 TripleDES、 和 DES|  
    |密碼|如果您將設定指定 SFTP 使用者密碼 **ClientAuthenticationMode** 至 **密碼**。|  
    |私密金鑰|如果您設定，請指定 SFTP 使用者的私密金鑰 **ClientAuthenticationMode** 至 **PublicKeyAuthentication**。|  
    |私密金鑰密碼|如果要求中指定索引鍵，指定私密金鑰密碼， **PrivateKey** 屬性。|  
    |SSH 伺服器主機金鑰指紋|指定配接器用來驗證伺服器的伺服器指紋 **AccessAnySSHServerHostKey** 屬性設定為 **False**。 如果指紋不符，連線會失敗。|  
    |使用者名稱|指定安全 FTP 伺服器的使用者名稱。|  
    
    **SSH 伺服器**
    
    |使用|動作|  
    |--------------|----------------|  
    |如果附加存在|如果目的地已經有正傳送至安全 FTP 伺服器的檔案，則此屬性指定正在傳送之檔案中的資料是否應附加至現有檔案。 如果設定為 **True**, ，資料會附加。 如果設定為 **False**, ，會覆寫目的地伺服器上的檔案。<br /><br /> **預設值︰** False|  
    |資料夾路徑|指定進行檔案複製的安全 FTP 伺服器上的資料夾路徑。|  
    |通訊埠|指定進行檔案傳輸的安全 FTP 伺服器上的連接埠位址。|  
    |伺服器位址|指定安全 FTP 伺服器的伺服器名稱或 IP 位址。|  
    |目標檔案名稱|指定用於將檔案傳輸至安全 FTP 伺服器的名稱。 您也可以使用目標檔案名稱的巨集。|  
  
4.  按一下  **確定** 和 **確定** 以儲存設定。  
  
## <a name="use-a-newer-winscp-version"></a>使用較新版的 WinSCP

若要搭配 BizTalk Server 使用較新版的 WinSCP，加入組件重新導向，讓 BizTalk 知道要載入哪些組件。 在 BizTalk Server 組態檔中設定重新導向： BTSNTSVC.exe.config （32 位元主控件執行個體） 和 BTSNTSVC64.exe.config （64 位元主控件執行個體）。

下列包含範例組態語法。 請務必取代`%NEWVERSION%`與您的版本：

```
<configuration>
 <runtime>
  <assemblyBinding>
   <dependentAssembly>
    <assemblyIdentity name="WinSCPnet" publicKeyToken="2271ec4a3c56d0bf" culture="neutral" />
    <bindingRedirect oldVersion="1.2.10.6257" newVersion="%NEWVERSION%"/>
   </dependentAssembly>
  </assemblyBinding>
 </runtime>
</configuration>
```

完成時，您的組態看起來如下所示：  

![在組態檔中的組件重新導向。](media/AssemblyRedirect.png)

## <a name="frequently-asked-questions"></a>常見問題集  
  
|問題|答|  
|--------------|------------|  
|支援哪些 SFTP 伺服器？|請參閱 [支援 SFTP 伺服器](http://social.technet.microsoft.com/wiki/contents/articles/29940.biztalk-serverbiztalk-services-supported-sftp-servers.aspx)。 從 BizTalk Server 2016 開始，SFTP 配接器會使用連接至 SFTP WinSCP。 如此一來，支援 WinSCP 的 SFTP 伺服器應該會運作。|  
|SFTP 配接器會使用相互驗證方法 （公開金鑰和密碼）？|-從 **BizTalk Server 2013 R2**, ，[是]。 如果設定為 **MultiFactorAuthentication** 必須提供 **Username** 使用其 **密碼** 和 **PrivateKey**。 此外，如果密碼保護私密金鑰，指定的密碼也 **PrivateKeyPassword** 屬性。<br /><br /> -針對 **BizTalk Server 2013**, ， **密碼** 或 **PublicKeyAuthentication** 可用。 **MultiFactorAuthentication** 隨附於 BizTalk Server 2013 的 SFTP 配接器不支援。|  
|支援何種私用金鑰格式？ 可以使用 OpenSSH 私密金鑰格式？|SFTP 配接器支援的 PuTTY 私密金鑰檔案格式。 PuTTYgen 可以用來將 OpenSSH 轉換為.ppk 格式。|  
|針對 [sshserverhostkeyfingerprint]，應該使用哪一個指紋演算法與格式？|您應該使用伺服器的金鑰 MD5 指紋的格式︰ `ssh-rsa 2048 90:e4:9b:67:d9:22:a7:5f:6f:33:db:6a:b1:23:96:12`。|  
|SFTP 配接器是否支援 256 位元加密？|是-SFTP 配接器支援 256 位元加密。 支援的加密演算法包括︰<br /><br /> -AES 加密︰ SDCTR 或 CBC 256 位元、 192 位元或 128 位元<br /><br /> -3DES (Triple DES) 加密︰ 168 位元 SDCTR 或 CBC|  
|配接器支援哪些 SSH 版本？|只有 SSH2。 無法與 SSH1 版本的 SFTP 伺服器建立連線。|  
|檔案遮罩是區分大小寫的嗎？|資料分割 \*.txt 和 \*.TXT 的運作方式很類似。 請安裝最新的 BizTalk Server 2013 累積更新。 BizTalk Server 2013 RTM 版本有區分大小寫的檔案遮罩。|  
|匯出繫結有空白密碼欄位。 嘗試匯入這些繫結來建立接收位置時，到底需要做哪些變更？|藉由編輯 [密碼] 欄位中編輯繫結檔案。 此外，在 `<Password vt="1">MySecretPassword</Password>`, ，**vt ="1"** 表示 null 值。 將它變更成 **vt ="8"**, ，表示為字串。 例如：<br /><br /> `<Password vt="8">MySecretPassword</Password>`<br /><br /> 如需詳細資訊，請參閱 [http://msdn.microsoft.com/library/system.runtime.interopservices.varenum(v=vs.100).aspx](http://msdn.microsoft.com/library/system.runtime.interopservices.varenum\(v=vs.100\).aspx)|  
|如何指定檔案路徑？|一般而言，指定路徑的格式 `/folder/pathname`。 不過，不同的伺服器需要不同的格式，包含或不含開頭或尾端斜線。 因此，您也可以嘗試下列︰<br /><br /> -                   `/folder/pathname`<br /><br /> -                   `/folder/pathname/`<br /><br /> -                   `folder/pathname`<br /><br /> -                   `folder/pathname/`|  
  

