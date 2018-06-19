---
title: 疑難排解 SAP 配接器的效能問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting, performance
- performance, troubleshooting
ms.assetid: 7e8e9fec-0edf-4c67-837c-0e271b2ffe68
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef9e18a2f26af993da36a13d389f2aff2ad2f60a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217118"
---
# <a name="troubleshoot-performance-issues-with-the-sap-adapter"></a>疑難排解 SAP 配接器的效能問題
本章節將討論使用來解決使用時，可能會遇到效能問題的疑難排解技巧[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。  
  
##  <a name="BKMK_SAPSlowdown"></a>速度變慢或拖延輸送量與 BizTalk Server 使用配接器時  
 **問題**  
  
 當使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，配接器所傳送或接收的訊息數目變慢或移至的拖延。  
  
 **可能的原因**  
  
 **EnableBizTalkCompatibilityMode**繫結屬性未設定 Wcf-custom 傳送或接收埠，BizTalk Server 管理主控台中。  
  
 **解決方式**  
  
 設定**EnableBizTalkCompatibilityMode**繫結屬性為 True。 如需有關這個屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。 如需如何設定繫結屬性的指示，請參閱[設定 SAP 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)。  
  
##  <a name="BKMK_SAPMemLeak"></a>使用參數的 NULL 值時，可能的記憶體流失  
 **問題**  
  
 您可能會注意到記憶體流失，如果您未指定輸入或資料表參數的值時叫用 SAP 系統中的成品。  
  
 **解決方式**  
  
 請確定您指定所有輸入與資料表參數的值時叫用 SAP 系統中的成品。  
  
## <a name="see-also"></a>另請參閱  
[SAP 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)