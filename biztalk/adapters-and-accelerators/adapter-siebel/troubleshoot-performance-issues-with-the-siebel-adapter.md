---
title: "Siebel 配接器疑難排解效能問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, performance issues
- performance, troubleshooting
ms.assetid: fe413b15-f703-4148-99df-17b5be3c74c1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6443dd8b96b19b3cf42f6444ba1ae6c16f2b4ee6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-performance-issues-with-the-siebel-adapter"></a>Siebel 配接器疑難排解效能問題
本章節將討論使用來解決使用時，可能會遇到效能問題的疑難排解技巧[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。  
  
## <a name="known-issues"></a>已知問題  
  
###  <a name="slowdown-or-stall-in-throughput-when-using-the-adapter-with-biztalk-server"></a>速度變慢或拖延輸送量與 BizTalk Server 使用配接器時  
 **問題**  
  
 當使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，配接器所傳送或接收的訊息數目變慢或移至的拖延。  
  
 **可能的原因**  
  
 **EnableBizTalkCompatibilityMode**繫結屬性未設定 Wcf-custom 傳送或接收埠，BizTalk Server 管理主控台中。  
  
 **解決方式**  
  
 設定**EnableBizTalkCompatibilityMode**繫結屬性為 True。 如需有關這個屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。 如需如何設定繫結屬性的指示，請參閱[siebel 設定繫結屬性](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md)。  
  
## <a name="see-also"></a>另請參閱  
[Siebel 配接器進行疑難排解](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)