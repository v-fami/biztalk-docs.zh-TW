---
title: 匯入和匯出 BizTalk Server 組態 |Microsoft Docs
description: 步驟來套用，匯入、 匯出或取消設定元件，並更新資料庫和 BizTalk Server 中的服務帳戶
ms.custom: ''
ms.date: 08/14/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6206ed8-d087-44cc-8ab5-da5d8a28e09a
caps.latest.revision: 40
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60faef2bf700a5e7fa1f5ced556e9fdd572201b4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980735"
---
# <a name="import-and-export-biztalk-server-configuration"></a>匯入和匯出 BizTalk Server 組態
BizTalk Server 組態可提供本機電腦上所安裝功能之組態狀態的高階分析。 此工具可讓您設定與取消設定功能、設定安全性設定，以及匯入和匯出組態。  
  
## <a name="prerequisites-to-use-the-biztalk-server-configuration"></a>若要使用 BizTalk Server 組態的必要條件  
   
-   做為登入您的帳戶必須是本機 administrators 群組的成員，並在 SQL Server 上具有系統管理員權限。  
  
-   BizTalk Server 所產生和列在 BizTalk Server 組態中的預設帳戶是本機群組。 在多伺服器環境中，取代網域群組中的這些本機群組。  
  
-   如果設定，做為登入您的帳戶必須是 OLAP 電腦上 OLAP 系統管理員群組的成員。  
  
    > [!NOTE]
    >  如果您變更群組成員資格的目前登入的使用者和群組也是網域的成員，是確定登出，然後重新登入之後所做的變更都完成後。 如果您未登入外/登入，您可能被拒絕存取，新的群組成員資格不會反映目前的登入。  
  
## <a name="apply-the-configuration"></a>套用組態  
  
1.  在 [BizTalk Server 組態] 中，按一下 [套用組態]。  
  
2.  在 [摘要] 畫面上，檢閱組態，然後按 [下一步]。  
  
3.  在 [完成] 畫面上，按一下 [完成]。  
  
## <a name="import-configuration"></a>匯入組態

> [!IMPORTANT]
> 當您匯入組態檔時，確認組態檔不會設定您要設定 BizTalk Server 尚未安裝的元件。 若是嘗試設定 BizTalk Server 上並不存在的元件，可能會導致鎖死情況。 在此情況下，取消設定相依於組態檔嘗試設定此元件的元件。 不過，嘗試取消設定相依元件可能要求該遺失元件必須存在且設定。 若要解決此問題，您必須編輯組態檔，以移除對解除安裝的元件，參考，或設定檔案套用到 BizTalk Server 的相容安裝。  
> 
>  密碼和備份檔案位置不會儲存在您要匯入，除非您手動編輯檔案的組態檔中。 如果已經設定的功能，它們不會匯入。  
  
  
1.  在 [BizTalk Server 組態] 中，按一下 [匯入組態]。  
  
2.  在 [開啟] 對話方塊中，選取要匯入的組態檔，然後按一下 [開啟]。  
  
3.  在 [BizTalk Server 組態] 中，按一下 [套用組態]。  
  
4.  在 [摘要] 畫面上，檢閱組態，然後按 [下一步]。  
  
5.  在 [完成] 畫面上，按一下 [完成]。  

您可以匯入 BizTalk Server 組態檔使用 「 BizTalk Server 組態架構。 如需使用這些檔案的詳細資訊，請參閱[處理組態架構](../install-and-config-guides/working-with-the-configuration-framework.md)。  
  
## <a name="export-configuration"></a>匯出組態

> [!NOTE]
>  密碼不會儲存在組態檔。    
 
1. 在 [BizTalk Server 組態] 中，按一下 [匯出組態]。  
  
2. 在 [另存新檔] 對話方塊中，輸入要儲存的檔案名稱，然後按一下 [儲存]。  

   您可以匯出使用 BizTalk Server 組態架構的 BizTalk Server 組態。 如需有關使用這些檔案的詳細資訊，請參閱[處理組態架構](../install-and-config-guides/working-with-the-configuration-framework.md)  
  
## <a name="unconfigure-features"></a>取消設定功能  
 您可以移除 BizTalk Server 組態中的 BizTalk Server 功能，以將機器上的 BizTalk Server 功能取消設定。  
  
> [!NOTE]
>  取消設定功能之前，必須先關閉 BizTalk Server 管理主控台。  
  
 
1.  在 [BizTalk Server 組態] 中，按一下 [取消設定功能]。  
  
2.  在 [取消設定功能] 對話方塊中，選取要移除的功能，然後按一下 [確定]。  
  
    > [!NOTE]
    >  此時會出現對話方塊警告您將會取消設定您所選取的功能。 按一下 [是]繼續。  
  
3.  在 [摘要] 畫面上，檢閱組態，然後按 [下一步]。  
  
4.  在 [完成] 畫面上，按一下 [完成]。  
  
## <a name="update-databases"></a>更新資料庫  
 您可以在 BizTalk Server 組態中編輯 BizTalk Server 功能，以變更 BizTalk Server 功能的相關資料庫伺服器和資料庫。  
  
> [!NOTE]
>  支援利用 SQL Server 預設執行個體和具名執行個體設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
> 
>  此工具可讓您大量編輯資料庫。  
  
 
1.  在 [BizTalk Server 組態] 中，按一下 [檢視]，然後按一下 [資料庫]。  
  
2.  在 [資料庫] 對話方塊中，選取要編輯的功能，然後按一下 [編輯]。  
  
3.  在 [資料庫] 對話方塊中，輸入要使用的資料庫伺服器名稱和資料庫名稱，然後按一下 [確定]。  
  
4.  在 [資料庫] 對話方塊中，按一下 [關閉]。  
  
## <a name="update-service-accounts"></a>更新服務帳戶  
 您可以在 BizTalk Server 組態中編輯 BizTalk Server 功能的相關服務帳戶，以變更這些帳戶。  
  
> [!NOTE]
>  此工具可讓您大量編輯帳戶。  
  
1.  在 [BizTalk Server 組態] 中，按一下 [檢視]，然後按一下 [服務帳戶]。  
  
2.  在 [服務帳戶] 對話方塊中，選取要編輯的功能，然後按一下 [編輯]。  
  
3.  在 [使用者認證] 對話方塊中，輸入要使用的使用者名稱和密碼，然後按一下 [確定]。  
  
4.  在 [服務帳戶] 對話方塊中，按一下 [關閉]。  
  
## <a name="see-also"></a>另請參閱  
 [設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)   
 [處理組態架構](../install-and-config-guides/working-with-the-configuration-framework.md)   