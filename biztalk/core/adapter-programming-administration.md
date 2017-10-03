---
title: "配接器程式設計管理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38563b3c-6d52-4e4e-ac6e-74f46ce22c6a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b19e3285357bb067614aae9472eb099470fe27f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-programming-administration"></a>配接器程式設計管理
配接器是一種特殊的組態存放區應用程式： 也就是配接器是與其他單一登入和組態存放區應用程式共用命名空間的元件。 因此，您可以使用 ISSOConfigStore 存取配接器的相關資訊。 不過，與組態存放區應用程式不同的是，您不能在具有 ISSOAdmin 介面的配接器上執行管理功能。 而是必須透過 ISSOPSAdmin 管理配接器。 使用特定的配接器管理介面的原因是可讓系統為其他活動與組態存放區取得協調。  
  
## <a name="see-also"></a>另請參閱  
 [配接器程式設計組態](../core/adapter-programming-configuration.md)   
 [配接器群組和群組配接器](../core/adapter-groups-and-group-adapters.md)   
 [密碼同步配接器](../core/password-sync-adapters.md)