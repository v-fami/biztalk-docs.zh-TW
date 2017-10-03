---
title: "設定一般合作對象屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbabf7e5-6388-4900-ad47-cf5d5af396b5
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4bb40e943cc06f298db01142590e2a133c1ee05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-general-party-properties"></a>設定一般合作對象屬性
合作對象或交易夥伴代表商務關係中的參與組織。 合作對象屬性包含下列資訊：  
  
-   一般資訊，例如合作對象名稱  
  
-   與合作對象相關聯的傳送埠  
  
-   與合作對象相關聯的憑證  
  
 如需合作對象或交易夥伴的詳細資訊，請參閱[交易夥伴](../core/trading-partners-and-business-profiles.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-party-properties"></a>若要設定合作對象屬性  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。  
  
2.  在**一般**頁面**合作對象屬性**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|輸入合作對象名稱。|  
    |**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**|選取此核取方塊，以指定合作對象代表同時裝載了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的同一個交易夥伴。 **重要事項：**對於兩個合作對象 TPM 解決方案會使用管線的方塊外，隨附於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須選取此核取方塊，至少一個合作對象。 **注意：**某些屬性如果您清除此核取方塊，將會停用時建立此合作對象的協議。|  
    |**其他屬性 – 名稱/值**|請輸入名稱-值組來儲存合作對象的任何資訊。 您可以視需要新增任意數目的名稱-值組。 **注意：**名稱 / 值組不會由 BizTalk Server 進行任何處理; 此資料僅供資訊。|  
    |**Delete**|按一下選取的名稱-值組，加以刪除。|  
  
3.  在**傳送埠**頁面**合作對象屬性**對話方塊方塊中，執行下列動作。  
  
    > [!NOTE]
    >  在 [!INCLUDE[prague](../includes/prague-md.md)] 中，設定相關傳送埠的動作是在協議層級進行。 **傳送埠**可用為合作對象屬性的一部分是純粹是為了回溯相容性 頁面。 當您將傳送埠與協議相關聯後，傳送埠設定也會傳播到合作對象設定，而您就可以在此頁面看到該傳送埠關聯。 但是，並非反之亦然。 在您將傳送埠與合作夥伴相關聯後，該傳送埠無法自動出現在協議設定中。 如需有關如何將傳送埠與協議產生關聯的詳細資訊，請參閱[設定傳送埠關聯 (X12)](../core/configuring-send-port-association-x12.md)或[設定傳送埠關聯 (EDIFACT)](../core/configuring-send-port-association-edifact.md)。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**傳送埠-名稱**|從下拉式清單選取要繫結至此合作對象的傳送埠。|  
    |**傳送埠-URI**|顯示傳送埠位址。|  
    |**移除**|按一下以從合作對象移除選取的傳送埠。|  
    |**屬性**|按一下即可顯示**傳送埠屬性**選取的傳送埠 對話方塊。|  
  
4.  在**憑證**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**瀏覽**|按一下即可顯示**選取憑證**對話方塊，其中的本機電腦 」 或 「 其他人憑證存放區設定要套用至訊息傳送至合作對象選取簽章憑證。|  
    |**一般名稱**|顯示選取憑證的描述。|  
    |**憑證指紋**|顯示私密金鑰憑證的指紋，此私密金鑰憑證是用於合作對象解析與簽章驗證。 憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字 (0 到 9 的數字或是 A 到 F 的字母)。|  
    |**移除憑證**|按一下以移除顯示的憑證。|  
  
5.  按一下**套用**接受這些屬性，或按一下**確定**來完成組態設定。 任何一項動作都會驗證設定。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 屬性](../core/configuring-edi-properties.md)