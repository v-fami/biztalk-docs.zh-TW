---
title: "如何移除被遺棄的追蹤設定檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, tracking profiles
- tracking profiles, orphans
- tracking profiles, activities
- tracking profiles, deleting
- activities, tracking profiles
ms.assetid: e8923dab-5d02-41a3-840b-104b20624e6c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33ddea8751a017db21306c06cdcca5929de641ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-orphaned-tracking-profiles"></a>如何移除被遺棄的追蹤設定檔
追蹤設定檔會與活動相關聯。 如果活動已解除部署，關聯的追蹤設定檔可能會被遺棄，表示那些追蹤設定檔不再與活動相關聯。 您可以使用下列程序移除追蹤設定檔。  
  
### <a name="to-remove-an-orphaned-tracking-profile"></a>移除被遺棄的追蹤設定檔  
  
1.  重新部署 BAM 定義。 如需部署 BAM 定義的相關資訊，請參閱[如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md)。  
  
2.  使用追蹤設定檔編輯器 (TPE) 移除追蹤設定檔。 移除追蹤設定檔的詳細資訊，請參閱[如何套用和移除追蹤設定檔](../core/how-to-apply-and-remove-a-tracking-profile.md)。  
  
3.  解除部署 BAM 定義。 如需移除 BAM 定義的資訊，請參閱[如何移除 BAM 定義](../core/how-to-remove-bam-definitions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤設定檔編輯器](../core/tracking-profile-editor.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)