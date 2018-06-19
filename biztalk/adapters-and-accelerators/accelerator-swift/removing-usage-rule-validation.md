---
title: 移除的使用方式規則驗證 |Microsoft 文件
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
ms.openlocfilehash: 017184e5f530096dc0ca166fdaaa9810a3372cfa
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962116"
---
# <a name="removing-usage-rule-validation"></a>移除的使用方式規則驗證
使用規則 SWIFT 標準中定義且由強制執行[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]特定的每個訊息類型的商務原則。 這些使用規則是您可用來提供額外的驗證欄位的指導方針。 與不同的是網路驗證規則都是必要項，您可以選擇不使用規則所需的訊息類型。 如果是這樣，您可以執行下列其中一項：  
  
-   您可以移除特定的商務規則，以強制使用規則和訊息類型驗證原則。  
  
    > [!IMPORTANT]
    >  從原則移除規則將它永久移除。  
  
-   如果您不要在任何使用規則強制執行，您可以解除部署的訊息類型的驗證原則。  
  
### <a name="to-remove-a-rule-from-a-policy"></a>若要從原則移除規則  
  
1.  在文字編輯器中，例如 [記事本] 開啟您想要變更，例如，在 MT103_Validation_Policy 的驗證原則*\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for SWIFT \<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category 1\MT103。  
  
2.  移除規則 節點，不想，並再儲存原則。  
  
3.  使用商務規則引擎部署精靈來發佈和部署原則。  
  
    > [!NOTE]
    >  您也可以從 驗證原則移除規則，藉由建立一份原則中，移除特定規則，然後部署已修改的原則。 解除部署原則的舊版。  
  
    > [!NOTE]
    >  在商務規則編輯器 中，您無法刪除規則從已發行或部署的原則。  
  
### <a name="to-remove-the-policy-for-a-message-type"></a>若要移除的訊息類型的原則  
  
1.  按一下**啟動**，指向 **程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則編輯器 」**。  
  
2.  在原則總管 中，找到的訊息類型，例如 MT103_Validation_Policy 已部署的驗證原則。  
  
3.  以滑鼠右鍵按一下原則，請按一下**解除部署**，按一下 **刪除**，然後按一下 **是**。