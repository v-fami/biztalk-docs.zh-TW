---
title: "搭配 Oracle 資料庫配接器的效能問題疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance issues, troubleshooting
- troubleshooting, performance issues
ms.assetid: 2035cd2e-ce87-419b-aada-61d257671623
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ba487bcd5d6d245c979dec903613465ae54f8d9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-performance-issues-with-the-oracle-database-adapter"></a>搭配 Oracle 資料庫配接器的效能問題疑難排解
本章節將討論使用來解決使用時，可能會遇到效能問題的疑難排解技巧[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。  
  
## <a name="known-issue"></a>已知的問題  
 以下是最常見的效能問題時使用，可能會遇到[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連同其可能的原因和解決方式。  
  
##  <a name="BKMK_Slowdown"></a>速度變慢或拖延輸送量與 BizTalk Server 使用配接器時  
 **問題**  
  
 當使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，配接器所傳送或接收的訊息數目變慢或移至的拖延。  
  
 **可能的原因**  
  
 **EnableBizTalkCompatibilityMode**繫結屬性未設定 Wcf-custom 傳送或接收埠，BizTalk Server 管理主控台中。  
  
 **解決方式**  
  
 設定**EnableBizTalkCompatibilityMode**繫結屬性為 True。 如需有關這個屬性的詳細資訊，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。 如需如何設定繫結屬性的指示，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
### <a name="possible-memory-leak-on-a-64-bit-computer-when-using-the-oracle-database-adapter-to-perform-operations-involving-float-data-type"></a>當您使用 Oracle 資料庫配接器執行涉及浮點資料類型的作業時的 64 位元電腦上可能有記憶體流失  
 **問題**  
  
 使用時，您可能會遇到記憶體流失[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來執行作業，涉及 FLOAT 資料類型的 64 位元電腦上。  
  
 **解決方式**  
  
 安裝.NET \<*版本*\> (x64) 64 位元電腦上的。  
  
## <a name="see-also"></a>請參閱  
[疑難排解 Oracle 資料庫 adapter.md](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)