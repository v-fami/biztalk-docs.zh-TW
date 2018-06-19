---
title: WCF-CustomIsolated 配接器為何？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-CustomIsolated adapters, about WCF-CustomIsolated adapters
ms.assetid: 872fe97a-8a96-4b2a-8cc1-2db9b315c44f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fdf5a646f586030df6c9492fc6fb2999e49527a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289694"
---
# <a name="what-is-the-wcf-customisolated-adapter"></a>WCF-CustomIsolated 配接器為何？
WCF-CustomIsolated 配接器是用來啟用在具有外掛式主控件的 BizTalk Server 中使用 WCF 擴充性元件的功能。 此配接器可以發揮 WCF 架構的完整彈性。 它可以讓使用者選取及設定接收位置的 WCF 繫結，以及指定端點行為和安全性設定。 只有裝載在 Internet Information Services (IIS) 中的傳輸方式才能使用這個配接器。  
  
 WCF-CustomIsolated 配接器只包含一個接收配接器。 您可以使用這個 WCF-CustomIsolated 接收配接器，透過您針對在外掛式主控件中執行的接收位置所選取和設定的 WCF 繫結、服務行為、端點行為、安全性機制和輸入訊息內文來源，接收 WCF 服務要求。 使用 WCF-CustomIsolated 接收配接器的接收位置可以設定為單向或要求-回應 (雙向)。  
  
 如需有關 WCF 接收配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Wcf-customisolated 配接器](../core/configuring-the-wcf-customisolated-adapter.md)   
 [WCF 配接器](../core/wcf-adapters.md)