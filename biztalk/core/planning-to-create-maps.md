---
title: 規劃建立對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps, planning
ms.assetid: e86af976-b989-4e24-80d5-3a9a3ac4e443
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72dde6b09b7777204547d00d26af571c9998d73f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="planning-to-create-maps"></a>規劃建立對應
使用對應將符合某個結構描述的輸入訊息轉換成符合其他結構描述的輸出訊息。 這些轉換可能很簡單或相當複雜，其中包含資訊的計算與合併。  
  
 下表列出在您規劃建立對應時應回答的一些問題。  
  
|規劃問題|建議|  
|-----------------------|--------------------|  
|我需要建立哪些對應？|為您將使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 處理的商務文件建立一份清單。 例如，這類清單可能包含訂單、發票、交貨確認等。 此清單還可能包含多份這種商務文件，例如當您從某個交易夥伴接收的訂單結構不同於從另一位交易夥伴接收的訂單結構時。<br /><br /> 瀏覽此清單並決定哪些文件需要使用不同格式，或者哪些文件最好轉換成一般格式來處理。|  
|在哪些地方需要對應？|您可以在傳送埠、接收埠，以及代表商業流程的協調流程上使用對應。 考慮您想要或需要在哪些地方轉換文件。|  
|有需要轉換的舊對應嗎？|在 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 中建立的對應不需要修改即可進行移轉。 分配足夠的時間來測試移轉的對應。 不過，在舊版 BizTalk 中建立的對應可能並不一定是開啟 BizTalk Server 中。 **注意：**之前的版本中建立的對應[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]可能精確地在運作[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]或[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]2009年。 但是，這些對應可能不會在 BizTalk Server 中開啟。 <br /><br /> 對應包含**指令碼處理**運算質或自訂運算質可能需要額外的工作。 如需詳細資訊，請參閱[移轉運算質](../core/migrating-functoids.md)。|  
  
## <a name="see-also"></a>請參閱  
 [關於對應](../core/about-maps.md)   
 [移轉運算質](../core/migrating-functoids.md)