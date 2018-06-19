---
title: 疑難排解批次處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, troubleshooting
- troubleshooting, batching
ms.assetid: f47e1a16-47fd-4bd8-8dad-fcdba31a833e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94c8413a8022529e6ace56c50d5e6d75267a72e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206302"
---
# <a name="troubleshooting-batching"></a>疑難排解批次處理
解決相關問題[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]批次處理。  
  
## <a name="error-activating-batch"></a>啟動批次錯誤  
  
### <a name="symptom"></a>徵兆  
 無法啟動批次。 您收到一般網路錯誤。  
  
**可能的原因**:[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]已重新啟動，但[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管不是。  
  
**解析**： 重新啟動[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。  
  
## <a name="messages-are-not-batched-when-the-target-namespace-is-not-the-default"></a>目標命名空間不是預設值時，不會批次處理的訊息  
  
### <a name="symptom"></a>徵兆  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]未批次處理的訊息。  
  
**可能的原因**： 來源和目的合作對象不在相同的結構描述命名空間中。  
  
**解析**： 來源和目的合作對象必須使用相同的結構描述命名空間，若需要驗證。 確認來源和目的合作對象都使用相同的結構描述命名空間。  
  
## <a name="see-also"></a>另請參閱  
 [HL7 中的疑難排解和已知問題](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)