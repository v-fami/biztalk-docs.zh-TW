---
title: "設定識別項 (AS2) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29f12696-8257-4664-8e61-292678e98b6b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1f4c8ddde24c32f93d003f778b9359d70e87170
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-identifiers-as2"></a>設定識別項 (AS2)
在夥伴協議中，您必須指定傳送者與接收者合作對象。 這些值也會用來解析輸入或輸出訊息的協議。  
  
> [!IMPORTANT]
>  下列屬性會停用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
>   
>  -   **AS2To**下**其他協議解析程式**> 一節。  
>   
>  只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。 例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-the-identifier-properties"></a>設定識別項屬性  
  
1.  建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。 若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤上，按一下 **識別碼**。  
  
3.  在**AS2-從**頁面上，指定傳送 AS2 訊息的交易夥伴的名稱。  
  
4.  在**AS2-要**頁面上，指定交易夥伴接收 AS2 訊息的名稱。  
  
5.  在下**其他協議解析程式** 區段中，針對**AS2To**屬性，接收訊息的夥伴輸入其他別名。  
  
    > [!NOTE]
    >  此屬性是選擇項。 此屬性適用於回溯相容性。 合作對象定義當 BizTalk Server 2006 R2 或 BizTalk Server 2009 移轉至 BizTalk Server 中，在舊版的合作對象名稱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]隨附做為這個屬性的值。 這可確保協議解析，和現有的應用程式與夥伴定義可搭配 BizTalk Server。  
  
6.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>請參閱  
 [設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)