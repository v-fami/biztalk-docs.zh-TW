---
title: 什麼是 MSMQ 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, about MSMQ adapters
- MSMQ adapters
ms.assetid: 4f4bfe49-19fc-4195-8826-0329f17cbe94
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: caeac28ce33e2f5eeacbb73b03d9873ec1e74c92
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008399"
---
# <a name="what-is-the-msmq-adapter"></a>什麼是 MSMQ 配接器？
藉由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Adapter for MSMQ (MSMQ 配接器)，您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送和接收 Microsoft Message Queuing (亦稱為 MSMQ) 佇列的訊息。 MSMQ 配接器支援訊息佇列 4.0。 配接器適用交易式與非交易式、公用與私用以及本機與遠端佇列。 此外，MSMQ 配接器也提供大型訊息支援 (大於 4 MB)，而且可讓您存取訊息佇列 4.0 功能，例如，遠端交易讀取以及從子佇列讀取。  
  
 如果您將 BizTalk Server 安裝升級至 BizTalk Server，不會移除 BizTalk Server 2009 Adapter for MSMQ。 BizTalk Server 會安裝新版本的 MSMQ 配接器，因此您可以放心地解除安裝 BizTalk Server 2009 Adapter，msmq，然後手動移除這個版本的配接器的目錄結構。