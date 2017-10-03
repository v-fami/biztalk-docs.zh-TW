---
title: "版本控制服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versioning, service solutions
- service solution tutorial, versioning
ms.assetid: 0e09720f-53f2-4b38-aae3-a79ddfd35be5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af1c5d1475fc37322be9a8483963bbfd1432fbb4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="versioning-the-service-oriented-solution"></a>版本控制服務導向解決方案
做為前端加入方案中，兩個協調流程**CustomerServiceReceiveSend**和**CustomerServiceNativeRequestResponse**，呼叫中央使用協調流程， **CustomerService**。 協調流程呼叫取決於包含協調流程之組件的版本號碼。 由於這三個協調流程都在相同的組件中，因此沒有版本管理的問題。  
  
 此外，協調流程實作的商務程序是非常短暫的要求-回應程序，可以快速完成。 所以，管理商務程序版本在此解決方案中是沒有問題的，也就是說，不同版本的不同組件中不會有不同的協調流程。  
  
 不過，協調流程在結構描述組件中的確會使用結構描述。 若是結構描述經過修訂並編譯為不同的版本，則必須使用較新的結構描述組件版本重新編譯協調流程。  
  
## <a name="see-also"></a>另請參閱  
 [開發服務導向解決方案](../core/developing-a-service-oriented-solution.md)