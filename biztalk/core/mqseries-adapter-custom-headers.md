---
title: MQSeries 配接器自訂標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, custom headers
ms.assetid: b0e18203-a33f-4d50-8483-396699cdff23
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09a05b8c73cd7be84af01eb4465681816e429bc3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-custom-headers"></a>MQSeries 配接器自訂標頭
因為在 MQSeries 訊息中使用的標頭結構，您必須管理任何您想要使用的自訂標頭。 自訂標頭必須是訊息內文的一部分，以避免干擾 MQSeries 標頭的處理。 請確定您會避免降級任何自動升級的屬性。 如需自動升級屬性的詳細資訊，請參閱[MQSeries 配接器屬性](../core/mqseries-adapter-properties.md)。  
  
 接著，在訊息內文中自訂標頭的合併需要其他處理。 其中一個解決方案就是在應用程式的管線中處理自訂標頭。 接收管線會擷取自訂標頭資訊，並將資訊升級為內容屬性。 同樣地，傳送管線會取得對應到自訂標頭的內容屬性，並降級訊息內文中的屬性。  
  
 在管線元件中使用自訂標頭的範例，請參閱[MQSSendPipelineComponent （BizTalk Server 範例）](../core/mqssendpipelinecomponent-biztalk-server-sample.md)。  
  
## <a name="see-also"></a>另請參閱  
 [MQSeries 配接器屬性](../core/mqseries-adapter-properties.md)