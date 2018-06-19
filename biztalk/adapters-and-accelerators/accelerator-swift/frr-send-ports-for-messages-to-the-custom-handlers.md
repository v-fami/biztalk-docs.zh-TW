---
title: 訊息的自訂處理常式的 FRR 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FRR, send ports
- custom handlers
- FRR, custom handlers
- send ports, FRR
- send ports, custom handlers
ms.assetid: 486d7410-fde1-4a9b-a9c2-64c1ed85ebc0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6babc312ddad7d77a96e29bc9e59ec9298aa6ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207830"
---
# <a name="frr-send-ports-for-messages-to-the-custom-handlers"></a>訊息的自訂處理常式的 FRR 傳送埠
若要啟用 FRR 自訂處理常式，您必須建立一系列 FRR 傳送埠，其中每個將特定類型的原始訊息複本路由傳送至的自訂處理常式。 這兩個傳送埠都必須具有下列管線元件：  
  
-   「 組合 」 階段中的 SWIFT 組合器  
  
-   SWIFTSendFrrComponent 管線元件中的編碼階段  
  
 對於未成功傳送的類別 0 到 9 SWIFT FIN 訊息以外的所有訊息，傳送埠必須包含下列的篩選器：  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SendingServiceType = = [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService  
  
-   BTS。作業會設定每個訊息類型所需的值。 針對 BTS 的可能值。作業屬性，請參閱表格[FRR 傳送埠建立的自訂處理常式的傳送](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。  
  
 對於類別 0 到 9 SWIFT FIN 未成功傳送的訊息，傳送埠必須具有下列的篩選器：  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SendingServiceTyp = =[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrFailed = = true  
  
-   BTS。作業 = =[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendMTMsg  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason 設為所需的每個訊息類型的值。 針對 BTS 的可能值。作業屬性，請參閱表格[FRR 傳送埠建立的自訂處理常式的傳送](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。