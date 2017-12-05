---
title: "管理合作對象 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.resultsobject.party
helpviewer_keywords:
- Administration Console [BizTalk Server], parties
- managing [parties]
- managing [parties], about managing parties
- parties, managing
ms.assetid: 96d2bcb3-1e38-4dad-a0d6-e5913ba531e7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f639ad516ec4f4a61406b9690d2d52f2ea98599f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="managing-parties"></a>管理合作對象
使用**合作對象**節點，您可以設定商務夥伴 （合作對象） 或內部部門 （商務設定檔） 與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]解決方案互動。 如需詳細資訊，請參閱[交易夥伴](../core/trading-partners-and-business-profiles.md)。  

您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來建立和設定合作對象。 在 BizTalk Server 中建立合作對象之後，您可能會想使用協調流程與合作對象互動。 合作對象可透過角色與協調流程互動。 例如，協調流程中可能有託運角色。 與託運商相關聯的合作對象可能有一或兩個。 當協調流程需要決定僱用最便宜的託運公司來運送項目時，它可以比較託運商角色中合作對象的價格。  
  
 您必須登錄合作對象，使其與特定角色繫結。 登錄角色可讓協調流程與合作對象互動。 請參閱[如何登錄或取消登錄角色的合作對象](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md)。
 
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
## <a name="create-or-edit-a-party"></a>建立或編輯合作對象
  
1.  開啟 [BizTalk Server 管理] 。  展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 BizTalk 群組、 以滑鼠右鍵按一下**合作對象**，選取**新增**，然後選取**合作對象**。  
  
2.  在**一般**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|輸入合作對象名稱。|  
    |**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**|選取此核取方塊，以指定合作對象代表同時裝載了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的同一個交易夥伴。 **重要事項：**對於兩個合作對象 TPM 解決方案會使用管線的方塊外，隨附於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須選取此核取方塊，至少一個合作對象。 **注意：**某些屬性如果您清除此核取方塊，將會停用時建立此合作對象的協議。|  
    |**其他屬性 – 名稱/值**|請輸入名稱-值組來儲存合作對象的任何資訊。 您可以視需要新增任意數目的名稱-值組。 **請注意**： 名稱 / 值組不會由 BizTalk Server 進行任何處理; 此資料僅供資訊。|  
    |**Delete**|選取即可刪除選取的名稱 / 值組。|  
  
3.  在**傳送埠**頁面上，執行下列動作。  
  
    > [!NOTE]
    >  在 BizTalk Server 傳送埠關聯是在協議層級。 **傳送埠**可用為合作對象屬性的一部分是純粹是為了回溯相容性 頁面。 當您將傳送埠與協議相關聯後，傳送埠設定也會傳播到合作對象設定，而您就可以在此頁面看到該傳送埠關聯。 但是，並非反之亦然。 在您將傳送埠與合作夥伴相關聯後，該傳送埠無法自動出現在協議設定中。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**傳送埠-名稱**|從下拉式清單選取要繫結至此合作對象的傳送埠。|  
    |**傳送埠-URI**|顯示傳送埠位址。|  
    |**移除**|選取此選項，以從合作對象移除選取的傳送埠。|  
    |**屬性**|選取即可顯示**傳送埠屬性**選取的傳送埠 對話方塊。|  
  
4.  在**憑證**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**瀏覽**|選取即可顯示**選取憑證**對話方塊，其中的本機電腦 」 或 「 其他人憑證存放區設定要套用至訊息傳送至合作對象選取簽章憑證。|  
    |**一般名稱**|顯示選取憑證的描述。|  
    |**憑證指紋**|顯示私密金鑰憑證的指紋，此私密金鑰憑證是用於合作對象解析與簽章驗證。 憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字 (0 到 9 的數字或是 A 到 F 的字母)。|  
    |**移除憑證**|選取以移除顯示的憑證。|  
  
5.  選取**套用**接受這些屬性，或選取**確定**來完成組態設定。 任何一項動作都會驗證設定。  

### <a name="update-an-existing-party"></a>更新現有的合作對象
在合作對象登錄至角色且連接埠已繫結之後，您可以：  
  
-   編輯合作對象的名稱和描述  
-   編輯合作對象的憑證  
-   指定合作對象是否適用於組織裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]

1. 在**BizTalk Server 管理**，然後選取**合作對象**。

2. 在**合作對象與商務設定檔**窗格中，以滑鼠右鍵按一下您想要檢視或編輯合作對象，然後選取**屬性**。  

3. 檢視或編輯的屬性。 

4. 選取**套用**接受這些屬性，或選取**確定**來完成組態設定。 下列其中一個動作驗證設定。  

## <a name="delete-a-party"></a>刪除合作對象
刪除合作對象使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
> [!IMPORTANT]
>  您只能刪除未登錄於角色中的合作對象。 您必須先從登錄合作對象的角色來取消登錄它，才能刪除合作對象。 請參閱[如何登錄或取消登錄角色的合作對象](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md)。 

1. 在**BizTalk Server 管理**，選取**合作對象**，以滑鼠右鍵按一下您想要刪除，然後選取合作對的象**刪除**。  
  
2.  在**確認刪除合作對象**對話方塊中，選取**是**刪除合作對象。  

## <a name="search-for-a-party"></a>搜尋合作對象
如果您有大量的合作對象建立時，您可以使用**搜尋**選項，以顯示您想要查看的合作對象。  

1. 在**BizTalk Server 管理**，選取**合作對象**。

3.  在**合作對象與商務設定檔**窗格中的，於右上角，輸入搜尋字串中的**搜尋合作對象**文字方塊，然後選取 [搜尋] 圖示。 您也可以按 ENTER 開始搜尋。  
  
     當您使用搜尋時，您必須考量以下要點：  
  
    -   搜尋字串不區分大小寫
  
    -   您可以搜尋名稱 （在搜尋子字串） 中的文字。 例如，如果您搜尋 ‘ar’，[[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 會顯示以此搜尋字串開頭的合作對象 (例如 Artist) 或是名稱中包含此搜尋字串的合作對象 (例如 Party1)。  
  
    -   搜尋作業僅限於合作對象名稱。  
  
4.  若要清除搜尋結果，請選取 [搜尋] 方塊旁的紅色 'x'。  
  
## <a name="see-also"></a>請參閱  
 [管理角色連結](../core/managing-role-links.md)   
 [如何設定合作對象解析管線元件](../core/how-to-configure-the-party-resolution-pipeline-component.md)  
 [管理 EDI 和 AS2 解決方案](../core/managing-edi-and-as2-solutions.md)