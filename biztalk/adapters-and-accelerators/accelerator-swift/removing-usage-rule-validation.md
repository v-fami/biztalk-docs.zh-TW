---
title: 移除使用方式規則驗證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- policies, deleting rules
- rules
ms.assetid: b2b0dabf-8f99-4b85-95da-6bbf3e79ad41
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6e5ffc3e1ca36e200055a26e8e78f341b125d8a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975543"
---
# <a name="removing-usage-rule-validation"></a>移除使用方式規則驗證
使用規則定義於 SWIFT 的標準，並強制執行[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]每個訊息類型特有的商務原則。 這些使用規則是您可用來提供額外的驗證欄位的指導方針。 與網路驗證規則是必要項目，您可以選擇不使用規則所需的訊息類型。 如果是這樣，您可以執行下列其中一項：  

-   您可以移除特定的商務規則，以從訊息類型驗證原則的使用方式規則會強制執行。  

    > [!IMPORTANT]
    >  從原則移除規則將它永久移除。  

-   如果您不想要強制執行任何使用規則，您可以解除部署的訊息類型的驗證原則。  

### <a name="to-remove-a-rule-from-a-policy"></a>若要從原則移除規則  

1.  在文字編輯器中，例如 記事本 開啟 驗證原則，您想要變更，例如，在 MT103_Validation_Policy *\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for SWIFT \<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category 1\MT103。  

2.  移除規則 節點，不想，，然後儲存原則。  

3.  使用商務規則引擎部署精靈來發佈和部署原則。  

    > [!NOTE]
    >  您也可以移除從驗證原則的規則所建立的原則複本、 移除特定規則，然後再部署已修改的原則。 解除部署原則的舊版。  

    > [!NOTE]
    >  在 商務規則編輯器中，您無法刪除規則從已發佈或已部署的原則。  

### <a name="to-remove-the-policy-for-a-message-type"></a>若要移除的訊息類型的原則  

1. 按一下 **開始**，指向**程式**，指向**Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**商務規則編輯器 」**。  

2. 在原則總管 中，找出已部署的驗證原則的訊息類型，例如 MT103_Validation_Policy。  

3. 以滑鼠右鍵按一下原則，請按一下**Undeploy**，按一下**刪除**，然後按一下**是**。
