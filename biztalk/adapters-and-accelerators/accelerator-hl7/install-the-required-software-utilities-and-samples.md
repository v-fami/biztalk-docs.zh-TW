---
title: "安裝必要的軟體、 公用程式，與範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de0cb89d-08bd-48ec-a149-8929e2608df8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 678037cd050ae8375b3c9ec465860d939d48cccc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-required-software-utilities-and-samples"></a>安裝必要的軟體、 公用程式和範例
本教學課程需要[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Windows Server 和自訂[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]包含 MLLP 測試工具的安裝。 此外，您應該熟悉[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]中的開發[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]和[HL7 加速器，可用的 BizTalk 工具深入了解](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)。
  
 您必須具有下列公用程式和電腦上安裝的範例：  
  
-   **MllpSend 工具**  
  
     此命令列公用程式會傳送訊息透過最低限度的較低層通訊協定 (MLLP) 通訊協定 MLLP 的接收位置。 您可以使用它來測試您的教學課程結果。 如需詳細資訊，請參閱[MllpSend 工具](../../adapters-and-accelerators/accelerator-hl7/mllpsend-tool.md)。  
  
-   **MllpPReceive 工具**  
  
     此命令列公用程式會透過 MLLP 通訊協定，做為接收位置接聽程式接收訊息。 您可以使用它來測試您的教學課程結果，顯示訊息和接收的通知。 如需詳細資訊，請參閱[MllpReceive 工具](../../adapters-and-accelerators/accelerator-hl7/mllpreceive-tool.md)。  
  
-   **範例應用程式接受 ACK.txt**  
  
     這個範例檔案包含文字的應用程式接受通知訊息。 此範例會搭配 MllpReceive 工具，可接收並不會顯示訊息，然後送回通知範例檔中。  
  
 您需要安裝兩個工具和範例檔使用 BTAHL7 自訂安裝程序。 典型的安裝程序不會安裝這些工具。 若要安裝這些工具，請在執行 BTAHL7 自訂安裝，**自訂安裝**畫面上，選取**MLLP 測試工具**從**配接器**資料夾，然後選取**測試執行個體**從**成品**資料夾。 如需詳細資訊，請參閱[安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。  
  
## <a name="see-also"></a>另請參閱  
 [準備使用批次的教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)