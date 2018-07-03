---
title: ESB 管線 Interop 元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 25f9fb9d-d3d4-4df8-8e81-38b432f42ccf
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 794ce6407d10fc820444384550357f10d24f7723
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024238"
---
# <a name="esb-pipeline-interop-components"></a>ESB 管線 Interop 元件
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供支援元件和服務，包括下列：  
  
- **JMS 管線元件。** 這些元件會識別、 驗證及公開中繼資料和符合 IBM MQ Series 傳訊系統所使用的 JMS MQRFH2 格式的訊息的內容。 這項功能可讓[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]應用程式接收訊息，並透過 MQ Series 傳送訊息給 JMS 系統。 元件自動升級標頭資訊，並從訊息內容降級。  
  
- **命名空間管線元件。** 這些元件可以新增或移除的命名空間中的 XML 訊息的內容。 這可讓應用程式來修復衝突的命名空間或新增遺漏的命名空間，以防止在 Messagebox 資料庫和應用程式協調流程中的命名空間衝突。 元件也可讓 BizTalk Server，而不需修改外部發行系統取用 POX (純舊 XML)。  
  
  如需 ESB 管線元件的詳細資訊，請參閱[使用管線支援元件](../esb-toolkit/using-the-pipeline-support-components.md)。