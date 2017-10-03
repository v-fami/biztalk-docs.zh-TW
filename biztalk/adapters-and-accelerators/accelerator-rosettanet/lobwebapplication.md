---
title: "LOBWebApplication |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services, LOBWebApplication
- ASPX pages, LOBWebApplication utility
- virtual servers
- ASPX pages, submitting actions
- LOBWebApplication
- ASPX pages, response messages
- LOBWebApplication utility
ms.assetid: 2d578efd-72a9-4621-9274-30792bf94b6c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b00e29b51eac2c58ac7843cca75994efceb4085
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lobwebapplication"></a>LOBWebApplication
您可以使用 LOBWebApplication 公用程式，透過 ASPX 頁面將動作或回應訊息提交給交易夥伴，藉以模擬實際的商務營運系統 Web 應用程式。  
  
 設定 ASPX 頁面之後，您要啟動該頁面，然後輸入訊息的參數：主要組織和夥伴組織；PIP 代碼、版本和執行個體識別碼；以及訊息類別。 然後，您便可以修改服務內容，並提交訊息。  
  
## <a name="location-in-sdk"></a>SDK 中的位置  
 \<*磁碟機*> \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication  
  
## <a name="adding-a-virtual-server-for-lobwebapplication"></a>新增 LOBWebApplication 的虛擬伺服器  
  
#### <a name="to-add-a-virtual-server"></a>新增虛擬伺服器  
  
1.  按一下**啟動**，指向  **AllPrograms**，指向 **系統管理工具**，然後按一下 **網際網路資訊服務 (IIS) 管理員**.  
  
2.  在 Information Services 管理員中，依序展開**\<電腦名稱 > （本機電腦）**，依序展開**網站**，然後以滑鼠右鍵按一下**Default Web Site**。  
  
3.  指向**新增**，然後按一下 **虛擬目錄**。  
  
4.  在**虛擬目錄建立精靈**頁面上，按一下**下一步**，然後輸入別名站台，例如**LOBWebApplication**。  
  
5.  在**網站內容目錄**頁面上，按一下**瀏覽**，移至\<*磁碟機*> \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication，按一下 **確定**，然後按一下 **下一步**。  
  
6.  在**虛擬目錄存取權限**頁面上，選取**讀取**和**執行指令碼**，然後按一下 **下一步**。 按一下 **[完成]**。  
  
7.  將之前用來設定 BTARN 的服務帳戶使用者 (例如 hostsvc) 新增至 STS_WPG。  
  
8.  刪除 C:\WINDOWS\Microsoft.NET\Framework\v2.0.\Temporary ASP.NET Files 中的所有檔案。 您可能必須先執行 iisreset 程式，才能解除鎖定那些檔案並加以刪除。  
  
9. 在 [IIS 管理員] 中，將 LOBWebApplication 設定為在應用程式集區 BTARNHTTPReceivePool 下執行。  
  
10. 在 [IIS 管理員] 中，於 LOBWebApplication 公用程式的 [目錄安全性屬性] 區域中停用虛擬目錄的選項，以便用匿名身分執行。  
  
## <a name="building-lobwebapplication"></a>建置 LOBWebApplication  
  
#### <a name="to-build-lobwebapplication"></a>建置 LOBWebApplication  
  
1.  啟動 [!INCLUDE[vs2012](../../includes/vs2012-md.md)]。  
  
2.  在**檔案**，指向 **開啟**，然後按一下 **開啟的方案**。  
  
3.  移至\<*磁碟機*> \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication，選取**LOBWebApplication.sln**，然後按一下  **開啟**。  
  
    > [!NOTE]
    >  如果您尚未新增 LOBWebApplication 的虛擬伺服器，方案將無法正確地在 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 中開啟。  
  
4.  以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。  
  
5.  在**加入參考**對話方塊中，按一下 **瀏覽**，移至\<*磁碟機*>: \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\Bin，選取 Microsoft.Solutions.BTARN.ConfigurationManager.dll 和 Microsoft.Solutions.BTARN.Shared.dll 檔案，然後按一下**開啟**。  
  
6.  以滑鼠右鍵按一下**LOBWebApplication**，然後按一下 **建置**。  
  
## <a name="running-lobwebapplication"></a>執行 LOBWebApplication  
  
#### <a name="to-run-lobwebapplication-and-submit-a-message"></a>執行 LOBWebApplication 並提交訊息  
  
1.  按一下**啟動**，指向 **所有程式**，然後按一下  **Internet Explorer**。  
  
2.  在 Internet Explorer 中**位址**方塊、 輸入 http://localhost/LOBWebApplication，，然後按一下**移**。  
  
3.  在**提交訊息**對話方塊方塊中，輸入主要組織、 夥伴組織、 PIP 代碼、 PIP 版本、 PIP 執行個體識別碼和訊息類別。  
  
4.  視需要修改服務內容。  
  
5.  按一下 [提交]。  
  
## <a name="remarks"></a>備註  
 LOBWebApplication 公用程式會透過指定的 PIP 產生訊息的執行個體，再將產生的訊息執行個體中的服務內容輸入 ASPX 頁面。 為了執行這項操作，公用程式會使用與直接從 PIP 產生格式正確之訊息執行個體相同的技術。 如需詳細資訊，請參閱[從 PIP 建立格式正確的訊息執行個體](../../adapters-and-accelerators/accelerator-rosettanet/creating-a-well-formed-message-instance-from-a-pip.md)。 在 ASPX 頁面中，您可以將實際資料填入服務內容的任何欄位，以產生實際的訊息執行個體。  
  
 您可以使用 LOBWebApplication 公用程式，模擬商務營運系統 Web 應用程式提交訊息。 您可以使用 LOBApplication 公用程式，模擬商務營運系統桌面應用程式以提交訊息。  
  
## <a name="see-also"></a>另請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [LOBApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobapplication.md)