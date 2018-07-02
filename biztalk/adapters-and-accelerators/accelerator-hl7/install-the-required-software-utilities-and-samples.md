---
title: 安裝必要的軟體、 公用程式及範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de0cb89d-08bd-48ec-a149-8929e2608df8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45f92f4cc994b4139c1c33423cc7a94c9072e226
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965903"
---
# <a name="install-the-required-software-utilities-and-samples"></a>安裝必要的軟體、 公用程式及範例
本教學課程需要 Microsoft Windows Server 和自訂的 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]包含 MLLP 測試工具的安裝。 此外，您應該先熟悉[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]在 Microsoft 的開發[!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]並[了解 HL7 加速器以及可用的 BizTalk 工具](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)。
  
 您必須具備下列公用程式和安裝在您的電腦上的範例：  
  
- **MllpSend 工具**  
  
   此命令列公用程式會傳送一則訊息透過最少的較低層通訊協定 (MLLP) 通訊協定來 MLLP 接收位置。 您可以使用它來測試您教學課程的結果。 如需詳細資訊，請參閱 < [MllpSend 工具](../../adapters-and-accelerators/accelerator-hl7/mllpsend-tool.md)。  
  
- **MllpPReceive 工具**  
  
   此命令列公用程式會透過 MLLP 通訊協定，做為接收位置接聽程式接收訊息。 您可以使用它來測試您教學課程的結果，顯示訊息和接收的通知。 如需詳細資訊，請參閱 < [MllpReceive 工具](../../adapters-and-accelerators/accelerator-hl7/mllpreceive-tool.md)。  
  
- **範例應用程式接受 ACK.txt**  
  
   此範例檔案包含文字的應用程式接受通知訊息。 此範例適用於 MllpReceive 工具，可接收並顯示訊息，然後送回 st2 範例檔案中。  
  
  您需要安裝兩個工具和範例檔案，藉由使用 BTAHL7 自訂安裝程序。 一般安裝程序不會安裝這些工具。 若要安裝這些工具，請在執行 BTAHL7 自訂安裝中，**自訂安裝**畫面上，選取**MLLP 測試工具**從**配接器**資料夾，然後選取**測試執行個體**從**成品**資料夾。 如需詳細資訊，請參閱 <<c0> [ 安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。  
  
## <a name="see-also"></a>另請參閱  
 [準備使用批次處理教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)