---
title: 記錄對記錄連結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a3fa4d7-5689-4f55-af1b-369defa37037
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac6abc3d27ad3ee2f135e3ff5c8c1749fcae5f4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268486"
---
# <a name="record-to-record-linking"></a>記錄對記錄連結

## <a name="overview"></a>概觀
在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可以使用 BizTalk 對應工具來建立一次的來源和目的地結構描述的相似部分之間的多個連結。 在舊版的 BizTalk Server 中，您必須一次一個個別地建立這類連結。 記錄對記錄連結有兩種不同類型，根據所連結的來源與目的結構描述記錄的結構相似程度，每一種各適用於不同的實例，如下所示：  
  
-   **結構連結。** 當您的來源與目的結構描述中所連結的記錄結構完全相同或非常相似時，使用結構連結。  
  
-   **名稱相符連結。** 當您的來源與目的結構描述中所連結的記錄結構相似而且記錄與欄位名稱相符，但結構例外狀況多過於可使用的結構連結時，則使用名稱相符連結。  
  
    > [!NOTE]
    >  記錄對記錄連結適用於值複製連結僅設定使用**來源連結**屬性。  
  
## <a name="record-to-record-linking-structure-links"></a>記錄對記錄連結：結構連結  
 當您在來源與目的結構描述中所要連結的記錄結構完全相同或幾乎完全相同時，使用結構連結。  
  
 若結構描述的結構完全相同，只需要在每個結構描述的根節點增加一個連結。 在捷徑功能表中，選取想要的連結模式。  
  
 若結構描述中特定記錄的結構完全相同，只需要在每個結構描述中的那些記錄之間增加一個連結。 在捷徑功能表中，選取想要的連結模式。  
  
 有關如何設定記錄對記錄連結的使用結構連結，或按一下 名稱比對連結，請參閱[自動連結記錄](../core/how-to-link-records-automatically.md)。  
  
> [!NOTE]
>  結構連結為記錄對記錄連結的預設類型。  
  
## <a name="record-to-record-linking-name-matching-links"></a>記錄對記錄連結：名稱相符連結  
 當您在來源與目的結構描述中所要連結的記錄結構十分相似，但不完全相同時，可使用名稱相符連結。 例如，在來源或目的結構描述中所要連結的節點內的附屬記錄或欄位，可能多過於另一個結構描述中的附屬記錄或欄位。  
  
 若要在結構幾乎相符之來源與目的結構描述的部分之間建立名稱相符連結 (可能的話，包括整個結構描述)，請建立以某個子階層父節點為起點，並以另一個子階層父節點為終點的連結。 在捷徑功能表中，選取想要的模式。 在連結節點之後，就會為來源與目的結構描述中，名稱相同且擁有相同子結構的所有附屬記錄與欄位自動建立連結。  
  
 有關如何設定記錄對記錄連結的使用結構連結，或按一下 名稱比對連結，請參閱[自動連結記錄](../core/how-to-link-records-automatically.md)。  
  
## <a name="see-also"></a>另請參閱  
 [自動連結記錄](../core/how-to-link-records-automatically.md)   
 [編輯連結屬性](../core/how-to-edit-link-properties.md)