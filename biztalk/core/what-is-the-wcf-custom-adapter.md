---
title: 何謂 WCF-Custom 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-Custom adapters, about WCF-Custom adapters
ms.assetid: 7b2178dd-f737-4784-9bcb-e2b3979bfb0d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e090f82bc43d96dc14295af2fac2807cf1fd137
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288894"
---
# <a name="what-is-the-wcf-custom-adapter"></a>何謂 WCF-Custom 配接器？
WCF-Custom 配接器是用來啟用 BizTalk Server 中的 WCF 擴充性元件。 此配接器可以發揮 WCF 架構的完整彈性。 它可以讓使用者針對接收位置和傳送埠選取及設定 WCF 繫結， 也能讓使用者設定結束點行為和安全性設定。  
  
 WCF-Custom 配接器是由兩個配接器所組成：接收配接器和傳送配接器。  
  
 **WCF 自訂接收配接器**  
  
 使用 WCF-Custom 接收配接器可以透過您在接收位置的 [傳輸屬性] 對話方塊中所選取和設定的繫結、服務行為、結束點行為、安全性機制和輸入訊息內文的來源，接收 WCF 服務要求。 使用 WCF-Custom 接收配接器的接收位置可以設定為單向或要求-回應 (雙向)。  
  
 **Wcf-custom 傳送配接器**  
  
 使用 WCF-Custom 傳送配接器可以透過您所選取和設定的無類型繫結合約、服務行為、結束點行為、安全性機制和輸出訊息內文的來源，呼叫 WCF 服務。  
  
 如需有關 WCF 接收和傳送配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 WCF 自訂配接器](../core/configuring-the-wcf-custom-adapter.md)   
 [WCF 配接器](../core/wcf-adapters.md)