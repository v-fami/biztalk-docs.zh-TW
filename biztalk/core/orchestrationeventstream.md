---
title: "OrchestrationEventStream |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7c63610-6344-4b71-8d65-3add7883bc79
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1fd0dc229c38b3a060c75a9c584259175d72fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="orchestrationeventstream"></a>OrchestrationEventStream
如果您的應用程式是在安裝 BizTalk Server 的電腦上執行，而且您要追蹤屬於 BizTalk 協調流程一部分的項目，請使用 OrchestrationEventStream (OES) API。  
  
 OES API 會先將追蹤資料儲存在 BizTalk MessageBox 資料庫中。 然後再由 Tracking Data Decode Service (TDDS) 定期處理資料，並將資料保存到 BAM 主要匯入資料庫中。  
  
 OES API 位於 Microsoft.BizTalk.Bam.EventObservation 命名空間。 若要使用此 API，您必須將 Microsoft.Biztalk.BAM.Xlangs.dll 新增到您的專案。  
  
## <a name="oes-members"></a>OES 成員  
 OES API 是由 [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) 類別衍生而來。  
  
 OES 會實作 EventStream 類別內的所有方法，但在行為上則有下列例外狀況：  
  
 **公用靜態 void clear （);**  
  
 無作業。  
  
 **公用靜態 void Flush();**  
  
 無作業。  
  
## <a name="see-also"></a>另請參閱  
 [EventStream 類別](../core/eventstream-classes.md)