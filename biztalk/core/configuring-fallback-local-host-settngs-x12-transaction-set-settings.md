---
title: 設定後援本機主機設定 （X12-交易集設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 68511199-a7ed-45b3-807d-70378b2c6ebb
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fa9e1fcc8bf1764a16142d38058e14878341fdc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233390"
---
# <a name="configuring-fallback-local-host-settngs-x12-transaction-set-settings"></a>設定後援本機主機設定 (X12-交易集設定)
為了處理內送的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須要判斷它需要用來處理和驗證該交換的結構描述。 這個過程包括判斷與該結構描述相關聯的目標命名空間，以及判斷要使用的結構描述。 在後援協議的這個頁面中，您要指定後援目標命名空間。 如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]判斷結構描述所述[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。  
  
> [!NOTE]
>  這個主題也適用於 HIPAA 相關設定。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a>若要設定交易集的本機主機設定  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。  
  
2.  在**X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤，下方**交易集設定**區段中，按一下**本機主機設定**.  
  
3.  選取**轉換隱含的小數格式 Nn 10 進制數值**来轉換成 BizTalk Server 中的中繼 XML 中的基底 10 數值將格式 Nn 指定的 EDI 數字。  
  
    > [!NOTE]
    >  轉換後，中繼 XML 可能會在長度驗證時失敗。 這是因為以 10 為基底的數值格式包含小數點，這使得它的長度比 Nn 格式數字大一。 您可以藉由新增的值來解決這個問題**1**最小/最大長度值。  
  
4.  選取**建立針對尾端分隔符號的空 XML 標記**將交換傳送者包含尾端分隔符號的空 XML 標記。  
  
5.  如**目標命名空間**、 輸入 （或從下拉式清單中選取） 目標命名空間的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用來決定處理所接收的訊息之結構描述。  
  
6.  按一下**套用**接受變更，或按一下**確定**輸入並驗證這些變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 X12 後援協議屬性的交易設定。](../core/configuring-x12-fallback-agreement-properties-for-transaction-set-settings.md)