---
title: 設定 FTP 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 09/28/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FTP adapters, configuring
- configuring [FTP adapters]
ms.assetid: 7e7d2e2d-142e-4459-be25-efd501b396d2
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f81353597bf836c2032b8ad79cb1c779749ed6fc
ms.sourcegitcommit: c1e83b63ae34bd586e6e0ccc914640efdf96bd4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48423954"
---
# <a name="configuring-the-ftp-adapter"></a>設定 FTP 配接器


## <a name="before-you-begin"></a>開始之前
- FTP 配接器支援從安全的 FTP 伺服器讀取和寫入資料。 此配接器可支援透過安全通訊端層 (SSL)/傳輸層級安全性 (TLS) 從 FTP 伺服器傳輸檔案。 
- FTP 配接器支援從唯讀檔案位置下載檔案。 
- FTP 配接器針對 ASCII 模式支援不可部分完成檔案傳輸的也。

請參閱[最佳做法和 FTP 配接器的建議](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)。


## <a name="configure-the-receive-location"></a>設定接收位置

您可以設定 FTP 接收位置配接器屬性，在 BizTalk Server 管理主控台中。 如果不設定接收位置中的屬性，則會使用 BizTalk Server 管理主控台中的預設接收處理常式值。  

> [!NOTE]
>  再完成下列程序，您必須已經新增接收埠。 請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
> 1.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，然後展開您想在其中建立接收位置的應用程式。  

2. 在左窗格中，按一下**接收埠**節點。 在右窗格中，以滑鼠右鍵按一下與現有接收位置相關聯的接收埠或您想要與新接收位置產生關聯，然後按一下 **屬性**。  

3. 在 **接收埠屬性**對話方塊的左窗格中，選取**接收位置**。 在右窗格中，按兩下現有接收位置或按一下**新增**以建立新接收位置。  

4. 在**接收位置屬性**對話方塊中，於**傳輸**區段旁邊**型別**，選取**FTP**從下拉式清單和然後按一下**設定**。  

5. 在  **FTP 傳輸屬性**，執行下列動作：  

   **批次**

   |使用|動作|  
   |--------------|----------------|  
   |**最大的檔案**|指定每個 BizTalk Server 批次的檔案數目上限。<br /><br /> 零 (0) 表示無限制。<br /><br /> **預設值：** 0|  
   |**大小上限**|指定每個 BizTalk Server 批次的最大位元組數。<br /><br /> 零 (0) 表示無限制。<br /><br /> **預設值：** 0|  

   **防火牆**

   |使用|動作|  
   |--------------|----------------|     
   |**位址**|指定防火牆的位址，可指定 DNS 名稱或 IP 位址。|  
   |**模式**|指定配接器與 FTP 伺服器之間的連接模式。<br /><br /> **有效值：** Passive 和 Active<br /><br /> 在主動模式下，FTP 伺服器會連線到 FTP 配接器所開啟的連接埠。 在被動模式下，FTP 配接器會連線到 FTP 伺服器所開啟的連接埠。 如果您使用內部 IP，而且您連接到外部的 IP，主動模式可能無法運作。 在此情況下，您需要 FTP 支援的應用程式層閘道 (ALG) 中使用被動模式還是主動模式。<br /><br /> **預設值：** Active|  
   |**密碼**|指定防火牆的密碼。|  
   |**通訊埠**|指定防火牆的連接埠。<br /><br /> **有效值：** 1 到 65535 （含)<br /><br /> **預設值：** 21|  
   |**型別**|指定部署的防火牆類型。<br /><br /> **有效值：** 無、 Socks 4 和 Socks 5<br /><br /> **預設值：** None|  
   |**使用者**|指定防火牆的使用者名稱。|  

   **FTP**


   |         使用         |  動作  |
   |---|---|
   |       **帳戶**        |  指定 FTP 伺服器的帳戶名稱。 此選項已被取代，不建議使用這個屬性。  |
   |      **Get 之後**       | 指定檔案 GET 後要執行的 FTP 命令。 使用分號 (;) 來分隔命令。 |
   |      **Get 之前**      |   指定檔案 GET 前要執行的 FTP 命令。 使用分號 (;) 來分隔命令。 **注意：** 檔案 GET 前不支援 QUIT 命令。   |
   |   **錯誤閾值**    |   指定在停用位置之前，容許 BizTalk Server 發生的錯誤數目。<br /><br /> **預設值：** 10   |
   |      **檔案遮罩**       |  指定傳輸檔案時要使用的檔案遮罩篩選。  |
   |        **資料夾**        |   指定 FTP 伺服器上的輪詢位置。  |
   |   **FTP 伺服器類型**    | 新開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。 <br/><br/>您可以使用這個屬性來選擇 FTP 伺服器不需要 SYST 命令。 選項為 None、 AIX、 偵測、 GXS、 MVS、 用於 OS400，和其他。 <br/><br/>如果設定為**無**，使用 SYST 命令。 **其他**OS 類型不符合任何一個指定的類別目錄時，會使用。 <br /><br /> **預設值：** None |
   |         **Log**          |  指定要用來儲存記錄檔複本的位置。 您可以使用此檔案來診斷透過 FTP 傳送或接收檔案時所發生的錯誤情況。    |
   |    **最大檔案大小**     |   指定可下載的檔案大小上限，以 MB 為單位。<br /><br /> 零 (0) 表示檔案大小無限制。<br /><br /> **預設值：** 100    |
   |       **密碼**       |   指定要用來登入 FTP 伺服器的使用者密碼。 |
   |         **通訊埠**         |  指定此 FTP 伺服器的連接埠位址。<br /><br /> **預設值：** 21 |
   |    **表示法**    |  選取 FTP 接收資料的方式。<br /><br /> **有效值：** 二進位或 ASCII<br /><br /> **預設值：** 二進位  |
   |        **Server**        |   指定 FTP 伺服器的伺服器名稱或 IP 位址。 **注意：** URI 傳送埠或接收位置不能超過 256 個字元。  |
   |    **SSO 分支機構**     |  指定「企業單一登入」分支機構應用程式。  |
   | **使用名稱清單 (NLST)** |  指定配接器列出檔案的方式。 若不檢視系統定義的檔案清單，而要檢視檔案名稱，請將這個值設定為 [是]。<br /><br /> **預設值：** 否   |
   |      **使用者名稱**       |  指定要用來登入 FTP 伺服器的使用者名稱。  |

   **輪詢**

   |使用|動作|  
   |--------------|----------------|         
   |**下載後刪除**|指定配接器在從 FTP 伺服器下載檔案之後，是否要刪除檔案。<br /><br /> **預設值：** 是**附註：**|  
   |**啟用時間戳記比較**|指定配接器是否要根據修改的時間戳記，再次下載檔案。 如果配接器不具有 FTP 伺服器的刪除權限，MDTM (修改時間) 命令可讓配接器知道檔案自從上次下載後是否曾被修改。  根據此屬性的值，再次下載檔案。<br /><br /> **預設值：** No**注意**： 如果 FTP 伺服器不支援 MDTM，設定**重新下載間隔**屬性。 **注意︰** ，這個值時才適用**下載後刪除**設為 [否]。|  
   |**間隔**|指定輪詢此位置的時間間隔數。 若要連續輪詢，請將此值設為零 (0)。<br /><br /> **預設值：** 60|  
   |**重新下載間隔**|指定配接器再次下載檔案的間隔。 這個值時才適用兩者**下載後刪除**並**啟用時間戳記比較**會設定為 [否]。<br /><br /> **預設值：** -1<br /><br /> -1 表示配接器將不會再次下載檔案。<br /><br /> 0 表示配接器會在每個輪詢循環下載檔案一次。|  
   |**單位**|指定的單位類型**間隔**並**重新下載間隔**屬性。<br /><br /> **有效值：** 秒、 分鐘、 小時和天數<br /><br /> **預設值：** 秒|  

   **SSL**

   |使用|動作|  
   |--------------|----------------|
   |**用戶端憑證雜湊**|指定必須在安全通訊端層 (SSL) 交涉中使用之用戶端憑證的 SHA1 雜湊。<br /><br /> 系統會根據此雜湊，從用於執行 BizTalk 主控件執行個體之使用者帳戶的個人存放區挑選用戶端憑證。|  
   |**FTPS 連線模式**|指定對 FTPS 伺服器的 SSL 連線模式。<br /><br /> **有效值：** 隱含或明確<br /><br /> **預設值：** 明確|  
   |**使用資料保護**|如果配接器必須使用 SSL 加密來與 FTPS 伺服器之間往返傳送資料檔，請將這個屬性指定為 [是]。 將這個屬性指定為 [否]，配接器就會以純文字 傳送和接收資料檔 。 **注意︰** 此屬性才**使用 SSL**屬性設定為 [是]。 <br /><br /> **有效值：** Yes 或 No<br /><br /> **預設值：** [是]|  
   |**使用 SSL**|指定 FTP 配接器是否必須使用 SSL 來與 FTPS 伺服器通訊。<br /><br /> **有效值：** Yes 或 No<br /><br /> **預設值：** 否|  

   **調整參數**


   |         使用         | 動作  |
   |---|---|
   | **接收資料逾時** | 指定接收呼叫中止前時間 (以毫秒為單位)。 您可以使用此屬性，防止慢速伺服器造成接收位置停止回應。<br /><br /> **預設值：** 90000 |
   |   **暫存資料夾**   |  指定暫存資料夾的位置。 您可以使用此位置來保證可自傳輸失敗的地方回復傳輸。                                                |


6. 按一下 **確定**儲存設定。  

7. 在 **接收位置屬性**對話方塊方塊中，輸入適當的值，以完成接收位置的組態，然後再按一下**確定**儲存設定。 如需**接收位置屬性** 對話方塊中，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  

> [!NOTE]
>  請勿設定多個 FTP 接收位置來輪詢相同的 FTP URL。 若多個 FTP 接收位置同時輪詢相同的 URL，則每個接收位置均可接收一個檔案複本，如此可能造成資料重複。 因為 FTP 通訊協定不提供從目標 URL 讀取檔案時鎖定檔案的功能，才會發生此狀況。  
>   
>  若要提供高可用性的 FTP 接收配接器，您應該設定 FTP 接收配接器執行中叢集 BizTalk 主控件執行個體。 請參閱[執行叢集主控件中的配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。  

## <a name="configure-the-send-port"></a>設定傳送埠

您可以在 BizTalk Server 管理主控台中設定 FTP 傳送埠配接器屬性。 如果未設定傳送埠的屬性，預設值就會傳送處理常式會使用 BizTalk Server 管理主控台中的值。  

1. 在 BizTalk Server 管理主控台中，建立新的傳送埠，或按兩下現有的傳送埠進行修改。 請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 設定所有的傳送埠選項，然後在**傳輸**一節**一般**頁面上，指定**FTP**如**類型**選項。  

2. 在上**一般**頁面上，於**傳輸**區段中，按一下**設定**旁邊**類型**。  

3. 在  **FTP 傳輸屬性**，執行下列動作：  

   **防火牆**

   |使用|動作|  
   |--------------|----------------|    
   |**位址**|指定防火牆的位址，可指定 DNS 名稱或 IP 位址。|  
   |**模式**|選取配接器與 FTP 伺服器間的連接模式。<br /><br /> **有效值：** Passive 和 Active<br /><br /> 在主動模式下，FTP 伺服器會連線到 FTP 配接器所開啟的連接埠。 在被動模式下，FTP 配接器會連線到 FTP 伺服器所開啟的連接埠。 如果您使用內部 IP，而且您連接到外部的 IP，主動模式可能無法運作。 在此情況下，您需要 FTP 支援的應用程式層閘道 (ALG) 中使用被動模式還是主動模式。<br /><br /> **預設值：** Active|  
   |**密碼**|指定防火牆的密碼。|  
   |**通訊埠**|指定防火牆的連接埠。<br /><br /> **有效值：** 1 到 65535 （含)<br /><br /> **預設值：** 21|  
   |**型別**|選取部署之防火牆的類型。<br /><br /> **有效值：** Socks 4、 4、socks 5、 無<br /><br /> **預設值：** None|  
   |**使用者**|指定防火牆的使用者名稱。|  

   **FTP**


   |       使用       | 動作 |
   |---|---|
   |     **帳戶**      |  選擇性。 指定 FTP 伺服器的帳戶名稱。 不鼓勵使用此屬性的選項。 |
   |    **Put 之後**     |  指定檔案 PUT 後要執行的 FTP 命令。 使用分號 (;) 來分隔命令。  |
   | **配置儲存體** |  指定是否配置儲存空間給舊版主控件系統。 為回溯相容性提供此選項。<br /><br /> **有效值：** 否是<br /><br /> **預設值：** 否  |
   |    **Put 之前**    |  指定檔案 PUT 前要執行的 FTP 命令，例如，要在 FTP 伺服器上變更預設值的命令。 使用分號 (;) 來分隔命令。 不需要開啟命令。 **注意：** 檔案 PUT 前不支援 QUIT 命令。  |
   |      **資料夾**      |  指定在 FTP 伺服器上移動檔案的位置。 |
   | **FTP 伺服器類型**  | 新開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。 <br/><br/>您可以使用這個屬性來選擇 FTP 伺服器不需要 SYST 命令。 選項為 None、 AIX、 偵測、 GXS、 MVS、 用於 OS400，和其他。 <br/><br/>如果設定為**無**，使用 SYST 命令。 **其他**OS 類型不符合任何一個指定的類別目錄時，會使用。 <br /><br /> **預設值：** None |
   |       **Log**        |  指定要用來儲存記錄檔複本的位置。 使用此檔案來診斷透過 FTP 配接器傳送或接收檔案時所發生的錯誤情況。    |
   |     **密碼**     |  指定要用來登入 FTP 伺服器的密碼。 |
   |       **通訊埠**       | 指定 FTP 伺服器的連接埠位址。<br /><br /> **預設值：** 21  |
   |  **表示法**  | 選取 FTP 配接器傳送資料的方式 (二進位還是 ASCII)。<br /><br /> **有效值：** 二進位或 ASCII<br /><br /> **預設值：** 二進位   |
   |      **Server**      |  指定 FTP 伺服器的伺服器名稱或 IP 位址。  |
   |  **SSO 分支機構**   |  指定「企業單一登入」分支機構應用程式。 |
   | **目標檔案名稱** |  為檔案指定別名。 保留預設名稱可確保每一個傳送的訊息均擁有唯一的訊息名稱。<br /><br /> **預設值：** %MessageID%.xml  |
   |    **使用者名稱**     |  指定要用來登入 FTP 伺服器的使用者名稱。 |

   **SSL**

   |使用|動作|  
   |--------------|----------------|
   |**用戶端憑證雜湊**|指定必須在安全通訊端層 (SSL) 交涉中使用之用戶端憑證的 SHA1 雜湊。<br /><br /> 系統會根據此雜湊，從用於執行 BizTalk 主控件執行個體之使用者帳戶的個人存放區挑選用戶端憑證。|  
   |**FTPS 連線模式**|指定對 FTPS 伺服器的 SSL 連線模式。<br /><br /> **有效值：** 隱含或明確<br /><br /> **預設值：** 明確|  
   |**使用資料保護**|如果配接器必須使用 SSL 加密來與 FTPS 伺服器之間往返傳送資料檔，請將這個屬性指定為 [是]。 將這個屬性指定為 [否]，配接器就會以純文字 傳送和接收資料檔 。 **注意︰** 此屬性才**使用 SSL**屬性設定為 [是]。 <br /><br /> **有效值：** Yes 或 No<br /><br /> **預設值：** [是]|  
   |**使用 SSL**|指定 FTP 配接器是否必須使用 SSL 來與 FTPS 伺服器通訊。<br /><br /> **有效值：** Yes 或 No<br /><br /> **預設值：** 否|  

   **調整參數**


   |       使用       | 動作  |
   |---|---|
   | **連線限制** | 指定伺服器最多可以開啟的並行 FTP 連線數目。 值為 0 時表示沒有限制。<br /><br /> **預設值：** 0**附註：** 這個屬性會取代舊版 BizTalk Server 中用來控管連接限制的登錄項目。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會忽略用來控制連接限制的登錄項目。 |
   | **暫存資料夾** |      指定 FTP 伺服器上的暫存資料夾位置。 檔案會先上傳到此處，然後移至目的地 FTP 資料夾。 如果傳輸失敗，配接器會以 ASCII 傳輸模式重新開始上傳檔案，並繼續以二進位傳輸模式下載檔案。 **注意：** 如果檔案傳輸是不可部分完成的暫存位置與 FTP 伺服器上的相關位置之間，則也是不可部分完成檔案上傳。      |

4. 按一下  **確定**並**確定**以儲存設定。   


## <a name="ftp-commands-required-by-the-ftp-adapter"></a>FTP 配接器所需的 FTP 命令  
FTP 配接器會受到 FTP 通訊協定限制的影響，所以在來源或目的 FTP 伺服器上必須具有某些 FTP 命令。  

FTP 配接器做為 FTP 用戶端運作，而且可能需要的下列命令可在 FTP 伺服器，才能正確運作： 


| 命令  |  需要由接收  |  所需的傳送  |
|---|---|---|
|   SYST   | ✔ <br/><br/>選擇性開始 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] | ✔<br/><br/>選擇性開始 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] |
|  存放區   |  |  ✔  |
|   RETR   |  ✔  |  |
|   使用者   |  ✔  |  ✔  |
|   PASS   |  ✔  |  ✔  |
|   CWD    |  ✔  |  ✔  |
|   QUIT   |  ✔  |  ✔  |
|   PORT   |  ✔  |  ✔  |
|   PASV   |  ✔  |  ✔  |
|   ABOR   |  ✔  |  ✔  |
|   TYPE   |  ✔  |  ✔  |
|   RNFR   |  ✔  |  ✔  |
|   RNTO   |  ✔  |  ✔  |
|   DELE   |  ✔  |  ✔  |
|   PWD    |  ✔  |  ✔  |
|   LIST   |  ✔  |  ✔  |
|   NLST   |  ✔  |  ✔  |
|   NOOP   |  ✔  |  ✔  |
|   APPE   |  |  ✔   |
|   ALLO   |  ✔  |  ✔  |
|   MDTM   |  ✔  |  |
| AUTH TLS |  ✔  |  ✔  |
|   PBSZ   |  ✔  |  ✔  |
|   PROT   |  ✔  |  ✔  |

 如需有關這些 FTP 命令的詳細資訊，請參閱：  

-   [RFC 959-檔案傳輸通訊協定](http://go.microsoft.com/fwlink/p/?LinkId=119603)(http://go.microsoft.com/fwlink/p/?LinkId=119603)  

-   [RFC 4217-保護 FTP 與 TLS](http://go.microsoft.com/fwlink/p/?LinkId=183154) (http://go.microsoft.com/fwlink/p/?LinkId=183154)  

-   [RFC 3659-FTP](http://go.microsoft.com/fwlink/p/?LinkId=183155) (http://go.microsoft.com/fwlink/p/?LinkId=183155)  

## <a name="configuring-an-ftp-adapter-to-work-with-legacy-hosts"></a>設定 FTP 配接器搭配使用舊版主機

本節說明您需要知道要促進 FTP 配接器與大型主機電腦之間的通訊。   
> [!NOTE]
>  在傳送檔案至 MVS 或 AS400 主機時，無法使用暫存資料夾功能。 不支援在此欄位進行輸入，此舉將導致錯誤。  

> [!IMPORTANT]
>  下列資訊提供做為指南，但是不可替代 AS400 或 IBM 文件中的資訊。  

## <a name="mvs"></a>MVS  
 若要傳送檔案至大型主機上的 FTP 伺服器，該主機必須支援 IBM Generation Data Group (GDG)。 在名稱欄位中，每個檔案名稱會在目的地檔案名稱 (完整路徑前後加引號) 附加 (+1)。  

## <a name="as400"></a>AS400  
 在 AS400 系統傳送檔案時，有三種方法可命名檔案以及定義路徑：  

-   **檔案名稱 欄位**： 當檔案傳送至 FTP 伺服器中，輸入中的檔案名稱**Filename**欄位。 檔案名稱必須符合 AS400 系統的檔案命名慣例，因為檔案將會儲存在「程式庫檔案系統」(Library File System) 中。  

-   **Quote 命令**： 使用 Quote 命令在遠端電腦上執行指令碼。 輸入 Quote 命令**Before GET**， **Before PUT**，**之後取得**，和**After PUT**欄位上的任何端點。 請以下列格式輸入 Quote 命令：  

    ```  
    QUOTE RCMD <command to be run on the remote system>.  
    ```  

-   **整合檔案系統 (IFS)**: IFS 是 AS400 系統，可讓電腦為基礎的檔案，因此與 PC 相同的命名慣例的儲存體上的區域。 若要使用 IFS 而不使用預設的「程式庫檔案系統」(Library File System)，要輸入的第一個命令是 `quote site namefmt 1`。 此命令告知 AS400 系統要使用 IFS 命名慣例。    


## <a name="more-good-stuff"></a>更多實用功能

[FTP 配接器屬性結構描述和屬性](../core/ftp-adapter-property-schema-and-properties.md)  

[最佳做法和建議，FTP 配接器](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)  

[FTP 配接器](../core/ftp-adapter.md)
