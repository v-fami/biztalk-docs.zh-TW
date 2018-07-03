---
title: 步驟 7： 建置與部署 LOBWebApplication SDK 範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, building solutions
- double action tutorial, deploying solutions
ms.assetid: f61de666-ebda-4831-9669-598e9284e4c1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a0716c854c20f5ea7fa7d2ad91576cb142f6a02
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996183"
---
# <a name="step-7-building-and-deploying-the-lobwebapplication-sdk-sample"></a>步驟 7： 建置與部署 LOBWebApplication SDK 範例
在此步驟中，您將建立 Fabrikam 用來提交夥伴介面程序 (PIP) 要求到 Contoso 的商務營運系統 (LOB) 應用程式。 您可以找到 LOBWebApplication 專案中 Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK 資料夾。 若要執行的 Web 應用程式，您必須建立 Microsoft Internet Information Services (IIS) 虛擬目錄，然後建置 LOBWebApplication 專案。  
  
### <a name="to-create-the-lobwebapplication-virtual-directory"></a>建立 LOBWebApplication 虛擬目錄  
  
1.  按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  
  
2.  在 [Internet Information Services 管理員] 視窗中，依序展開 **< 電腦名稱 > （本機電腦）**，然後展開**網站**。  
  
3.  以滑鼠右鍵按一下**Default Web Site**，指向**新增**，然後按一下**虛擬目錄**。  
  
4.  在 [ **Welcometo 虛擬目錄建立精靈**頁面上，按一下**下一步]**。  
  
5.  在 [**虛擬目錄別名**頁面上，於**別名**方塊中，輸入**LOBWebApplication**，然後按一下**下一步]**。  
  
6.  在 **網站內容目錄**頁面上，按一下**瀏覽**。 在 瀏覽資料夾 對話方塊中，移至 ***\<磁碟機\>*:\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBWebApplication**，然後按一下 **確定**。 按 [下一步] 。  
  
7.  在上**虛擬目錄的存取權限**頁面上，取消選取**讀取**，選取**執行指令碼 （例如 ASP)**，然後按一下**下一步**。  
  
8.  在 **您已成功完成虛擬目錄建立精靈**頁面上，按一下**完成**建立虛擬目錄。  
  
### <a name="to-exclude-the-lobwebapplication-web-site-from-the-sharepoint-configuration"></a>從 SharePoint 組態排除 LOBWebApplication 網站  
  
1.  按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下**SharePoint 管理中心**。  
  
2.  在 **管理中心**網頁上**虛擬伺服器組態**區段中，選取**擴充或升級虛擬伺服器**。  
  
3.  如果看不到電腦上設定的 URL，請按一下**完整清單**。  
  
4.  在 **虛擬伺服器清單**頁面上，選取**Default Web Site**。  
  
5.  在 **虛擬伺服器管理**區段中，按一下**定義管理的路徑**。  
  
6.  在 **加入新的路徑**區段中**路徑**方塊中，輸入 **/LOBWebApplication**。  
  
7.  針對**型別**，選取**排除的路徑**，然後按一下 **確定**。  
  
### <a name="to-build-the-lobwebapplication-project"></a>建置 LOBWebApplication 專案  
  
1.  按一下 **開始**，指向**所有程式**，指向**Microsoft Visual Studio 2008**，然後按一下**Microsoft Visual Studio 2008**。  
  
2.  在 [檔案] 功能表上，指向 [開啟舊檔]，再按一下 [專案/方案]。  
  
3.  在 [開啟專案] 對話方塊中，移至 ***\<磁碟機\>*:\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBWebApplication**，選取**LOBWebApplication.sln**解決方案檔案，然後按一下**開啟**。  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下**http://localhost/LOBWebApplication**，然後按一下**加入參考**。  
  
5.  在 [加入參考] 對話方塊中，按一下**瀏覽**。 在 [加入參考] 對話方塊中，移至 ***\<磁碟機\>*:\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\Bin**資料夾。  
  
6.  從 [Bin] 資料夾中，選取**Microsoft.Solutions.BTARN.ConfigurationManager.dll**並**Microsoft.Solutions.BTARN.Shared.dll**組件，然後再按一下**開啟。**  
  
7.  按一下 [ **[確定]** 以關閉**加入參考**] 對話方塊。  
  
8.  在 [方案總管] 中，以滑鼠右鍵按一下**解決方案 'LOBWebApplication'** ，然後按一下**建置方案**。  
  
9. 以滑鼠右鍵按一下**default.aspx**，然後按一下**設定為起始頁**。  
  
## <a name="see-also"></a>另請參閱  
 [測試雙向動作教學課程](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-double-action-tutorial.md)