---
title: ESB 路線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 379edc6a-7d53-4338-87a5-47b5238453a4
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80aa7c1ef4bc53ad2e2821eaf8dc4184777900a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294966"
---
# <a name="the-esb-itinerary-component"></a>ESB 路線元件
ESB 行程元件設定以 ESB 路線上手隨訊息一起傳送的 SOAP 標頭內容屬性。  
  
## <a name="installation"></a>安裝  
 自動安裝 ESB 核心安裝**路線**BizTalk Server 管線元件資料夾中的管線元件。  
  
## <a name="how-it-works"></a>運作方式  
 ESB 行程元件是一個接收管線中只可位於 Microsoft BizTalk 管線元件。 它會將值升級從 SOAP 訊息標頭或元件的設定為訊息內容屬性。 您可以找到的升級中隨附的行程上手 Web 服務 SOAP 標頭範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 這些 Web 服務公開 SOAP 標頭做為其合約的一部分，並且用戶端應用程式必須設定標頭。 當訊息通過接收管線中的元件，元件會讀取 SOAP 標頭值，並將升級 （寫入） 至訊息內容屬性。  
  
## <a name="using-the-esb-itinerary-component"></a>使用 ESB 路線元件  
 您可以 ESB 行程元件新增至接收管線，然後使用管線，接收位置中。 元件會自動升級 SOAP 標頭值或元件內送訊息的內容屬性的設定。  
  
 如需如何使用此元件的範例，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。