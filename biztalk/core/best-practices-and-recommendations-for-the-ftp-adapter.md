---
title: "最佳作法和 FTP 配接器的建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, FTP adapters
- FTP adapters, best practices
ms.assetid: f73b2016-d48c-48d8-9ba0-96e26b694d1e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85967756089be91939bf5b6f73b12d36ed8caa51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-and-recommendations-for-the-ftp-adapter"></a>最佳做法和建議，FTP 配接器
閱讀有關的最佳做法、 安全性建議和 FTP 配接器的增強功能。

## <a name="best-practices"></a>最佳做法  
  
-   定期刪除暫存資料夾中部分接收的檔案，以避免檔案因使用電腦資源，而導致可能中斷服務。  
  
-   使用資料流處理伺服器時，會拒絕對新檔案的讀取，直到 MessageBox 資料庫收到整個檔案為止。 若 FTP 配接器提交了部分檔案至 MessageBox 資料庫，則 MessageBox 資料庫將會成功儲存訊息，但是 FTP 配接器將無法刪除接收位置的部分訊息。  
  
-   若要確保 FTP 配接器接收處理常式的高可用性，應將 FTP 配接器接收處理常式設定為在已叢集的 BizTalk 主控件執行個體中執行。 如需詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。  

## <a name="security-recommendations-and-tips"></a>安全性建議和秘訣

BizTalk Server 可以從檔案傳輸通訊協定 (FTP) 伺服器接收檔案，並將檔案傳送至 FTP 伺服器的其他應用程式。 BizTalk Server 不能做為 FTP 伺服器。  
  
 FTP 的是，實際上就不安全： 使用者名稱、 密碼和其他認證周遊網路以純文字。 同樣的，上傳或下載的檔案是以純文字移動，可輕易地在途中被檢視或修改。 此外，攻擊者可以假冒 FTP 伺服器本身 (又稱為惡意伺服器攻擊)。 在這種情況下，您無法分辨特定 FTP 伺服器是否確實是您要通訊的電腦。  
  
 若要解決這些問題，FTP 配接器支援 SSL/TLS 通訊協定，可確保透過加密的資料機密性。  
  
 如需一般安全性考量，當您使用 FTP 通訊協定，請參閱[Internet FAQ Archives](http://go.microsoft.com/fwlink/p/?LinkId=24779) (http://go.microsoft.com/fwlink/p/?LinkId=24779)。   
  
 建議您使用下列指導方針，在環境中部署 FTP 配接器並保護其安全：  

- 保護您伺服器和限制存取資料。 由於 FTP 通訊協定並非安全的通訊協定，因此總是容易受到攻擊。 您可以使用專用連線和限制 BizTalk Server 與 FTP 主機之間的伺服器與連線，來確保 FTP 伺服器的安全。 您也可以設定 FTP 伺服器的安全性原則，以與 FTP 用戶端安全地連線。  

- 設定 FTP 配接器使用安全通訊端層 (SSL) 通訊協定，以在配接器與 FTP 伺服器之間進行通訊。 SSL 通訊協定可透過加密確保資料機密性無虞。 這表示使用者識別碼與密碼都會加密，而不會以純文字傳送。 使用 FTP 配接器，您也可以選擇加密 FTP 連線的資料通道。 請參閱**增強功能**（在本主題中）。
  
-   若要達成安全的檔案傳輸，設定 FTP 配接器所提供的 SSL 特定屬性。 請參閱**增強功能**（在本主題中）。 
  
-   FTP 配接器支援 FTP Request for Comments (RFC) 959。 請參閱[World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?LinkId=24781) (http://go.microsoft.com/fwlink/p/?LinkId=24781)。 FTP 配接器不支援「安全 FTP」(SFTP) 通訊協定。 請參閱[SFTP 配接器](../core/sftp-adapter.md)。
  
-   您可以跨防火牆使用 FTP 配接器。 根據您所使用的防火牆類型，您可能要設定一個或多個下列防火牆屬性： 使用者名稱、 密碼、 電腦、 連接埠、 防火牆類型 (無、 socks 4、 socks 5)，和模式。  
  
-   建議您將遠端 FTP 伺服器放在安全的位置。 您必須確定此伺服器的實體和網路安全性，讓惡意伺服器的攻擊降至最低。  
  
-   FTP 配接器支援使用「企業單一登入」(SSO)。 請參閱[實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)。  
  
-   根據預設，FTP 接收配接器因為會在下載後，從伺服器刪除檔案，所以必須具有 FTP 伺服器的寫入權限。 不過，FTP 配接器支援從唯讀位置下載檔案。 請參閱**增強功能**（在本主題中）。
  
- 使用 FTP 傳送埠時，必須在設定傳送埠時指定和儲存使用者識別碼與密碼組合。 配接器會使用此資訊，連線到 FTP 伺服器。 使用者認證是以純文字儲存於 SQL Server 資料庫中。 在動態傳送埠中，認證會傳送到 FTP 伺服器。 若生產環境需要較強的安全性，請對伺服器使用匿名認證。  
  
-   當系統提示您的帳戶時，我們建議您輸入現有的使用者帳戶，而不是本機系統帳戶。 如此可讓您實作較佳的安全性，並讓配接器以自動模式執行，而不需登入。  

## <a name="enhancements"></a>功能增強

### <a name="transferring-data-to-and-from-a-secure-ftp-server"></a>與安全的 FTP 伺服器傳輸資料  
 FTP 配接器支援從 FTPS 伺服器傳輸檔案透過安全通訊端層 (SSL) / 傳輸層安全性 (TLS)。 SSL/TLS 可透過加密確保資料的機密性。 您必須設定配接器所提供的 SSL 特有屬性，以啟用安全模式。 由於配接器同時允許在安全 FTP 伺服器讀取及寫入資料，因此在設定傳送處理常式/傳送埠以及使用接收處理常式/接收位置時，也可使用 SSL 特有屬性。  

從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，FTP 配接器已不再需要 SYST 命令： 

- **FTP 伺服器類型**屬性 – 設定此屬性，以使用不需要 SYST 命令的伺服器。
   
 可用來設定 SSL 特有屬性的選項如下：  

-   **使用 SSL**屬性 – 設定此屬性，所以 FTP 配接器必須使用 SSL，每個傳輸工作階段。  
  
-   **啟用資料保護**屬性 – 設定此屬性，以開啟 資料加密。 FTPS 伺服器的安全性原則必須允許配接器使用安全 SSL 連線，此設定才可正常運作。  
  
-   **FTPS 連線模式**屬性 – 設定此屬性來判斷何時啟動安全性：  
  
    -   在**隱含**模式中，安全性會自動開啟，因為介面卡連線到伺服器。  
  
    -   在**Explicit**模式中，配接器傳送至起始安全控制通道的命令。  
  
> [!NOTE]
>  FTP 配接器不支援對伺服器憑證進行撤銷檢查。  
  
### <a name="support-for-downloading-files-from-locations-marked-as-read-only"></a>支援從標示為唯讀的位置下載檔案  
FTP 配接器支援從唯讀的檔案位置的檔案下載。 配接器現在會將下載檔案的清單保存在資料庫中。 下次下載時，FTP 伺服器上的檔案清單會與配接器所維護的檔案清單進行比較，而僅下載伺服器上多出的新檔案。 若要支援現有的檔案兩次下載之間的更新位置的情況下，您可以設定同時檢查檔案時間戳記，設定配接器**啟用時間戳記比較**屬性為 ftp 接收位置。 在這種情況下，即使檔案名稱相同，但更新時間戳記時，配接器會下載檔案。  
  
 有時候 FTP 伺服器不支援讓修改過的時間戳記與檔案產生關聯。 在這種情況下，配接器可讓您指定過了多少時間就要重新下載檔案的間隔。 您可以設定此間隔設定**重新下載間隔**屬性為 ftp 接收位置。  
  
 下表列出的 FTP 配接器預期的行為不同的值設定為**下載後刪除**，**啟用時間戳記比較**和**重新下載間隔**屬性。  
  
|下載後刪除|啟用時間戳記比較|重新下載間隔|配接器行為|  
|---|---|---|---|  
|是|不適用|不適用|配接器會在下載檔案之後，從 FTP 伺服器刪除該檔案。 這是配接器的預設行為。|  
|否|是|不適用|配接器在下載檔案之後，不會從 FTP 伺服器刪除該檔案。 但是配接器會使用 MDTM 命令，比較檔案的上次修改時間戳記。 配接器會根據時間戳記重新下載檔案。|  
|否|否|適用|FTP 配接器會在過了您指定的間隔之後從 FTP 伺服器下載檔案，無論檔案是否經過修改。|  
  
### <a name="support-for-atomic-file-transfer-in-ascii-mode"></a>支援在 ASCII 模式下以不可部分完成的方式傳輸檔案  
 FTP 配接器針對 ASCII 模式支援不可部分完成檔案傳輸。 若要啟用針對 ASCII 模式的不可部分完成檔案傳輸，配接器使用**暫存資料夾**屬性。 此屬性會定義檔案要先移至 FTP 伺服器上的哪個暫存位置。 檔案在完整傳輸至暫存位置後，接著就會移至 FTP 伺服器上的相關位置。 這裡假設在 FTP 伺服器上的暫存位置與相關位置之間的檔案傳輸是以不可部分完成的方式進行。  
  
> [!NOTE]
>  使用 ASCII 檔案的暫存資料夾的擴充功能不只適用於**傳送**，並不適用於**接收**。 實作這項功能的主要原因是，第三方應用程式會讀取檔案完全寫入之前。 在 BizTalk 中正在接收檔案，配接器會將檔案提交至 BizTalk 完整讀取之後，才。  
  
> [!NOTE]
>  在二進位模式中，**暫存資料夾**屬性也可用來恢復檔案傳輸失敗時之間。 這並不適用於 ASCII 模式。 針對 ASCII 模式**暫存資料夾**屬性只適用於不可部分完成檔案傳輸。  
  
 
## <a name="next"></a>下一個 
[設定 FTP 配接器](../core/configuring-the-ftp-adapter.md)  

## <a name="see-also"></a>另請參閱  
 [接收和傳送伺服器的連接埠](../core/ports-for-the-receive-and-send-servers.md)   
 [最小安全性使用者權限](../core/minimum-security-user-rights.md)
