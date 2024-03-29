---
title: 步驟 2： 建立 Fabrikam LOBWebApplication |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating LOBWebApplication
- LOBWebApplication
ms.assetid: 2ff8bd20-7fbc-4e16-b177-bb4afac7f7c3
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c55234d8ee9c123c9efe9e7ec66b7c0db590b54
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966623"
---
# <a name="step-2-creating-the-fabrikam-lobwebapplication"></a>步驟 2： 建立 Fabrikam LOBWebApplication
在此步驟中，您將建立 LOB 應用程式，讓 Fabrikam 用來提交 3A2 PIP 要求至 Contoso。 LOBWebApplication 專案是安裝在 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK 中。 若要執行的 Web 應用程式，您必須建立 Microsoft Internet Information Services (IIS) 虛擬目錄，並建置 LOBWebApplication 專案。  
  
> [!NOTE]
>  如果您已完成「雙向動作」教學課程，則不必執行此步驟。  
  
### <a name="to-create-the-lobwebapplication-virtual-directory"></a>建立 LOBWebApplication 虛擬目錄  
  
1.  按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services 管理員**。  
  
    > [!NOTE]
    >  如果您已完成「雙向動作」教學課程，便已經在該教學課程中建立 LOBWebApplication 虛擬目錄。 若是如此，您就不必執行下列步驟。 您將此項目，不過，必須變更的虛擬目錄的權限**執行指令碼**要**讀取**。  
  
2.  在 [Internet Information Services 管理員] 中展開 **< 電腦名稱 > （本機電腦）**，然後展開**網站**。  
  
3.  以滑鼠右鍵按一下**Default Web Site**，指向**新增**，然後按一下**虛擬目錄**。  
  
4.  在 [ **Welcometo 虛擬目錄建立精靈頁面**，按一下**下一步]**。  
  
5.  在 [**虛擬目錄別名**頁面上，於**別名**方塊中，輸入**LOBWebApplication**，然後按一下**下一步]**。  
  
6.  在 **網站內容目錄**頁面上，按一下**瀏覽**，選取**\<磁碟機\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBWebApplication**資料夾，然後再按一下**確定**。 按 [下一步] 。  
  
7.  在 [**虛擬目錄的存取權限**頁面上，按一下**下一步]**。  
  
8.  按一下 **完成**建立虛擬目錄。  
  
### <a name="excluding-lobwebapplication-from-sharepoint"></a>從 SharePoint 排除 LOBWebApplication  
  
1.  按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下**SharePoint 管理中心**。  
  
    > [!NOTE]
    >  如果您已完成「雙向動作」教學課程，便已經在該教學課程中從 SharePoint 排除 LOBWebApplication 虛擬目錄。 若是如此，您就不必執行下列步驟。  
  
2.  在 **管理中心**頁面上，於**虛擬伺服器組態**區段中，選取**擴充或升級虛擬伺服器**。  
  
3.  如果看不到電腦上設定的 URL，請按一下**完整清單**。  
  
4.  選取  **Default Web Site**。  
  
5.  在 **虛擬伺服器管理**區段中，按一下**定義管理的路徑**。  
  
6.  在 **新增路徑**區段中**路徑**方塊中，輸入"/ LOBWebApplication"。 針對**型別**，選取**排除的路徑**，然後按一下 **確定**。  
  
### <a name="to-build-the-lobwebapplication-project"></a>建置 LOBWebApplication 專案  
  
1.  開始**Microsoft Visual Studio 2012**。  
  
2.  從**檔案**功能表上，指向**開放**，然後按一下**專案 \ 方案**。  
  
3.  在開啟專案 對話方塊中，在**查詢**，移至**\<磁碟機\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\ SDK\<SDKLOBWebApplication**，選取**LOBWebApplication.sln**解決方案，，然後按一下**開啟**。  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下最上層節點 (http://localhost/LOBWebApplication)，然後按一下**加入參考**。  
  
5.  在 [加入參考] 對話方塊中，按一下**瀏覽**並移至**\<磁碟機\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\bin**.  
  
6.  **選取 Microsoft.Solutions.BTARN.ConfigurationManager.dll 和 Microsoft.Solutions.BTARN.Shared.dll**組件**然後按一下 [確定]。**  
  
7.  在 **建置**功能表上，按一下**建置網站**。  
  
### <a name="to-run-the-lobwebapplication-project"></a>執行 LOBWebApplication 專案  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**default.aspx**，然後選取**設定為起始頁**。  
  
2.  在 **偵錯**功能表上，按一下**啟動但不偵錯**。  
  
## <a name="see-also"></a>另請參閱  
 [測試解決方案](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-solution.md)