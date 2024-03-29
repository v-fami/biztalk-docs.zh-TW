---
title: PrivateInitiator 範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f176566-2a71-487d-84c1-5e7767701e8b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ab84d145939191a8bdbca9afb44d04fdf24b3e9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011279"
---
# <a name="privateinitiator-sample"></a>PrivateInitiator 範例
PrivateInitiator.odx 範例包含安裝 Microsoft® BizTalk Server 啟動者私用程序的程式碼。 這是會從預設 SQL 配接器架構的傳送埠和接收埠，傳送和接收 RNIF 服務內容訊息的一般私用程序。  
  
 根據預設，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式安裝中的範例\<*磁碟機*\>: \Program Files\\Microsoft BizTalk\<版本\>Accelerator forRosettanet\sdk\privateinitiator。  
  
## <a name="sample-contents"></a>範例內容  
 啟動者私用程序屬於啟動者的內部商務程序。 私用程序能讓啟動者公開程序和後端商務營運系統程式進行後端整合。 啟動者私用程序會與公開程序進行通訊，以初始化訊息。  
  
 啟動者私用程序對於每個實作而言都是唯一的。 您可以依照您的目的自訂 PrivateInitiator.odx 範例。 但是您必須小心，不要對啟動者公開程序的功能造成不良影響。  
  
 如需詳細資訊，包括訊息流程的描述，請參閱[啟動者私用程序](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md)。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [私用程序](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)