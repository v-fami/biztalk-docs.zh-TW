---
title: "上安裝和設定 BizTalk Accelerator for SWIFT 訊息伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Accelerator for SWIFT, configuring
- BizTalk Accelerator for SWIFT, installing on Messaging servers
- BizTalk Messaging servers, installing BizTalk Accelerator for SWIFT
ms.assetid: 7a8f60aa-5ff2-4584-9d4a-dc4a0ba61aca
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef434603c1740375f4399f368e89f99a923cba86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers"></a>上安裝和設定 BizTalk Accelerator for SWIFT 訊息伺服器
本章節描述如何安裝及設定[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]傳訊的伺服器上。 這些伺服器主要用於通訊的 SWIFT 網路。  
  
### <a name="to-install-and-configure-biztalk-accelerator-for-a4swift-on-the-messaging-server"></a>安裝和設定 BizTalk Accelerator for A4SWIFT 傳訊的伺服器上  
  
1.  執行自訂安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。 安裝**MRSR**和**SWIFT 訊息**功能。  
  
    > [!NOTE]
    >  您不需要安裝 Web 元件 Message Repair 和 New Submission 的功能，因為此伺服器並沒有 MRSR 站台。  
  
    > [!NOTE]
    >  安裝完成後，「 組態精靈 」 會啟動。  
  
2.  在 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態主控台中，設定**MCRR**。