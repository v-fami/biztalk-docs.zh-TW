---
title: "疑難排解問題的 Data Provider for Siebel |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, troubleshooting
- troubleshooting, Data Provider for Siebel
ms.assetid: 2bfe69a2-d6de-466d-9f36-f11c386c771c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae6e100635b1cb2db5c78ff713c8e6ad32d4e7d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-issues-with-the-data-provider-for-siebel"></a>疑難排解問題的 siebel 資料提供者
本章節將討論使用來解決使用時可能遭遇的錯誤的疑難排解技巧[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])。  
  
## <a name="known-issues"></a>已知問題  
  
### <a name="data-provider-for-siebel-may-give-component-datareader-source-380-error"></a>Siebel 的資料提供者可能會產生 「 元件 ' DataReader Source' (380) 」 錯誤  
 **問題**  
  
 Siebel 商務元件上執行 SELECT 查詢時[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]可能會產生 「 元件 ' DataReader Source' (380) 」 錯誤。  
  
 **可能的原因**  
  
 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]提供此錯誤，如果收到來自 Siebel 系統參數的值超過參數的 maxLength 屬性。  
  
## <a name="see-also"></a>另請參閱  
[Siebel 配接器進行疑難排解](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)