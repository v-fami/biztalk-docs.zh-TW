---
title: BtarnClean |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BtarnClean utility
- assemblies, undeploying
- BTARN, deleting artifacts
- orchestrations, unenlisting
- ports, stopping
- orchestrations, stopping
- ports, deleting
- BTARN, BtarnClean utility
ms.assetid: fbecbb88-9b18-4b4b-a286-0bfa783f2320
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc3759d13498b6582eeb87fe162d287d64550044
ms.sourcegitcommit: 436ebffd959a9c4bdaafd4da9a5843c59a018eb7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "34855553"
---
# <a name="btarnclean"></a>BtarnClean
您可使用 BtarnClean 公用程式清除電腦的 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 成品。 這包含下列動作：  
  
-   停止和取消登錄所有的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 協調流程  
  
-   停止和刪除所有關聯的連接埠  
  
-   解除部署所有的 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.BTARN.* 組件  
  
## <a name="location-in-sdk"></a>SDK 中的位置  
 \<*磁碟機*\>\Program Files (x86) \ Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK  
  
## <a name="running-btarnclean"></a>執行 BtarnClean  
  
#### <a name="to-run-btarnclean"></a>若要執行 BtarnClean  
  
1.  開啟命令提示字元。  
  
2.  移至\<*磁碟機*\>\ Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\\。  
  
3.  在命令提示字元中，輸入**BtarnClean**，然後按 ENTER 鍵。  
  
     此公用程式會提示您確認您想要繼續。  
  
## <a name="remarks"></a>備註  
 如果您在具有相依於其他成品之 BizTalk 成品的電腦上執行 BtarnClean 公用程式，BtarnClean 就會指出它無法移除該成品。 此公用程式會讓該成品保留在原處，然後繼續移除其他成品。 您可移除相依性，然後再執行一次該公用程式。  
  
 如果您在屬於多電腦部署之一部分的電腦上執行 BtarnClean 公用程式，移除成品將影響該部署中的其他伺服器。  
  
 如果您在存在開發人員建立的多個程序時執行 BtarnClean 公用程式，此公用程式將不會移除仍在使用中的程序。  
  
 如果某個使用者的成品使用了主要接收位置，BtarnClean 公用程式將不會移除該接收位置。 在此情況下，您必須刪除接收埠。  
  
 如果您想在執行此公用程式後取消設定 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]，請從 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 資料夾執行 Configuration.exe /u。  
  
## <a name="see-also"></a>另請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
