---
title: 如何使用角色連結精靈 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- links [roles]
- Role Link Wizard [Orchestration Designer]
- roles, links
- Orchestration Designer, Role Link Wizard
- role links, Role Link Wizard [Orchestration Designer]
- links [roles], about links
ms.assetid: ddc33d87-c08d-4193-9483-4644ef302853
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d31abcc8fcc2bfaf1ebd641e1e52ad08d1c9c9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255854"
---
# <a name="how-to-use-the-role-link-wizard"></a>如何使用角色連結精靈
[角色連結精靈] 可以讓您建立新角色連結或修改現有的角色連結。 您可以使用它來設定或檢視角色連結的名稱、類型與存取限制，以及構成角色連結類型的實作角色與使用角色。 若要了解角色連結運作，請參閱[協調流程中使用角色連結](../core/using-role-links-in-orchestrations.md)。  
  
 **角色連結名稱**： 為您填入角色連結名稱，和為目前名稱的現有角色連結，您要設定或自動產生的名稱，如果您要建立新的角色連結。 不論是哪一種，您都可以修改名稱。  
  
 **角色連結類型**： 您可以選取現有的角色連結類型，或另外新建一個。 不論您是設定新的或現有的角色連結類型，都可以指定協調流程參與服務的方式。  
  
> [!NOTE]
>  建議您最好在建立角色連結之前先建立角色連結類型及關聯的連接埠類型，好讓您可以使用現有的角色連結類型來定義角色連結。 如需詳細資訊，請參閱[如何在協調流程中建立角色連結](../core/how-to-create-role-links-in-orchestrations.md)。  
  
 **角色連結使用方式**： 如果您建立新的角色連結類型，這兩種實作和使用角色為您自動建立。 您可以選取反映協調流程參與服務的方式之角色。 在您完成精靈中的步驟之後，可以重新命名角色識別項或移除角色，以更符合您的實作。 角色連結類型必須包含這兩種角色類型中的一種或每種角色類型各一。 當您按一下**確定**，未設定的角色會建立對應至每個名稱。 您也可以在 [類型] 視窗中選取角色的連接埠類型。  
  
> [!NOTE]
>  若您叫用 [連接埠組態精靈] 來為角色連結類型建立連接埠類型，並且想要選取先前已定義的連接埠類型，請確定連接埠類型的存取限制未與角色連結類型的存取限制衝突。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程中使用角色連結](../core/using-role-links-in-orchestrations.md)