---
title: 訊息的自訂處理常式的 FRR 傳送埠 |Microsoft Docs
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
ms.openlocfilehash: df8ba2b085268f2c0c272b81b27768db716b63c0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996151"
---
# <a name="frr-send-ports-for-messages-to-the-custom-handlers"></a>訊息的自訂處理常式的 FRR 傳送埠
若要啟用 FRR 自訂處理常式，您必須建立一系列的 FRR 傳送埠，其中每個將特定類型的原始訊息複本路由傳送至自訂處理常式。 這些傳送連接埠必須具有下列管線元件：  

- 中 「 組合 」 階段的 SWIFT 組合器  

- SWIFTSendFrrComponent 管線元件中的編碼階段  

  未成功傳送的分類 0 到 9 SWIFT FIN 訊息以外的所有訊息，傳送埠必須具有下列的篩選器：  

- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SendingServiceType = = [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService  

- BTS。作業會設定每個訊息類型所需的值。 針對 BTS 的可能值。作業屬性，請參閱表格[傳送至自訂處理常式建立 FRR 傳送埠](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。  

  為類別 0 到 9 SWIFT FIN 未成功傳送的訊息，傳送埠必須具有下列的篩選條件︰  

- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SendingServiceTyp = =[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService  

- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrFailed = = true  

- BTS。作業 = =[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendMTMsg  

- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason 設為每個訊息類型所需的值。 針對 BTS 的可能值。作業屬性，請參閱表格[傳送至自訂處理常式建立 FRR 傳送埠](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。
