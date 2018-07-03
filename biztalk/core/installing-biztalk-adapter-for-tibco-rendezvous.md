---
title: 安裝、 結構描述，以及限制 TIBCO Rendezvous 配接器 |Microsoft Docs
description: 安裝、 產生和結構描述，BizTalk adapter for TIBCO Rendezvous 在 BizTalk Server 中的限制
ms.custom: ''
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6404e7e-f671-4c57-a222-0bbe7cbc334f
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f1eafd0c4a5ff96c3083d28b23347a2908aa52c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022100"
---
# <a name="install-schemas-and-limitations-of-the-tibco-rendezvous-adapter"></a>安裝、 結構描述和 TIBCO Rendezvous 配接器的限制

## <a name="install-and-setup"></a>安裝及設定

[安裝及設定企業應用程式的介面卡](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md)包含的步驟安裝企業配接器，而且也包含 安裝配接器之前和之後安裝配接器所知道的重要資訊。 

## <a name="generate-schemas"></a>產生結構描述
TIBCO Rendezvous 系統不包含訊息類型儲存機制。 所有訊息建構和剖析都是在嵌入在 Rendezvous 應用程式層級。 由於此限制，配接器無法提供結構描述產生功能。  
  
您必須撰寫結構描述，並使用**加入現有項目**在 Visual Studio 中將它匯入協調流程中使用。 結構描述對於 BizTalk Server 開發工具以及 Visual Studio 中的整合十分重要。 BizTalk Server 開發人員可以選擇提供完整的結構描述、精簡的結構描述，或介於兩者之間的版本。  

## <a name="limitations"></a>限制

- 不保證欄位名稱的唯一性。 如果 TIBCO Rendezvous 訊息包含兩個相同的欄位名稱，結果產生的 XML 會無效。  
  
- 不會提供欄位排序。  
  
- 根據 TIBCO Rendezvous 文件，不可列印的字元不會使用在主體名稱中，但是，仍有使用這類字元的可能。 BizTalk Adapter for TIBCO Rendezvous 不支援含有這些字元的主體名稱。  
  
- 不支援對精靈的安全連線。  
  
- 不支援自訂資料型別。  
  
- 傳輸端不支援「認證傳訊」。  
- 
  ## <a name="next-step"></a>下一步

[教學課程：使用 Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md)  