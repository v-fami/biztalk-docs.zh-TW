---
title: 如何設定相互關聯類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, correlation types
- correlation types, configuring
- correlation types, deleting
- configuring, correlation types
ms.assetid: cfae4d2e-ec79-45c8-93b3-799dc5e0576e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 646ac7dafd5207a2558e45252077efe2d9616a70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248566"
---
# <a name="how-to-configure-correlation-types"></a>如何設定相互關聯類型
您使用**相互關聯屬性**對話方塊來加入或移除的相互關聯類型的屬性。 相互關聯類型會列出相互關聯集中的屬性；在執行階段中，傳送和接收活動會使用這些屬性，確定內送訊息是否與協調流程之正確執行個體相關。  
  
 此對話方塊中有兩個窗格，分別包含一份屬性清單。 左窗格為 [可用屬性] 窗格，內含您的專案所定義或參考之所有屬性的樹狀檢視。 顯示的屬性預設為 BizTalk Server 定義的系統屬性，但是您也可以在屬性結構描述中定義自己的屬性。 如需有關如何建立屬性結構描述的詳細資訊，請參閱[屬性結構描述](../core/property-schemas.md)。  
  
> [!NOTE]
>  結構描述屬性必須先升級，然後才能在相互關聯類型中使用。 如需詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)。  
  
### <a name="to-add-and-configure-a-correlation-type"></a>若要新增及設定相互關聯類型  
  
-   在協調流程檢視] 視窗中，以滑鼠右鍵按一下**相互關聯類型**，然後按一下 [**新相互關聯類型**。  
  
     **相互關聯屬性**對話方塊隨即出現。 新增您要包含在相互關聯類型內的屬性。  
  
    > [!NOTE]
    >  如果您存取**相互關聯屬性**對話方塊直接從相互關聯集，如果不存在，則會建立相互關聯類型的相互關聯集。 您的變更將會儲存在新的相互關聯類型中，而且會將相互關聯集設定為使用新的相互關聯類型。 如果相互關聯集已有相互關聯類型，在您進行變更後，系統將會修改該相互關聯類型。  
  
### <a name="to-remove-a-correlation-type"></a>若要移除相互關聯類型  
  
-   在協調流程檢視] 視窗中，以滑鼠右鍵按一下您想要移除，然後按一下 [相互關聯類型**刪除**。