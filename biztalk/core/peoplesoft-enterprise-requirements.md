---
title: "PeopleSoft Enterprise 需求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PeopleSoft Enterprise, requirements
- send handlers, PeopleSoft requirements
- CLASSPATH environment variable
- custom component interface object
- system requirements
- GET_CI_INFO.pc
ms.assetid: fabd808d-d9b6-43b0-a12a-727189f00a9d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45f267afce09e9c50d732d376fde43beaa1ef39a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="peoplesoft-enterprise-requirements"></a>PeopleSoft Enterprise 需求
## <a name="send-handler-peoplesoft-requirements"></a>傳送處理常式 PeopleSoft 需求  
 Microsoft BizTalk Adapter for PeopleSoft Enterprise 包含一個可供人透過 Java API 存取的自訂元件介面 (CI)。 將 `GET_CI_INFO` 這個自訂 CI 物件部署到 PeopleSoft 中 (以提供 BizTalk Adapter for PeopleSoft Enterprise 所需中繼資料資訊) 的方式，是透過 PeopleSoft 工具。 如需詳細資訊，請參閱[準備使用 PeopleSoft Enterprise](../core/preparing-to-use-peoplesoft-enterprise.md)。  
  
 上傳自訂元件介面是只發生一次。 `GET_CI_INFO.pc` 這個檔案會隨產品安裝，這個檔案必須要安裝好，您才能使用配接器瀏覽 CI。 您必須有 PeopleSoft Application Designer 的存取權，但該 Application Designer 應用程式不一定要安裝在 BizTalk Server 電腦上。 您可以使用該 Application Designer 將自訂 CI 上傳到您瀏覽的 PeopleSoft 電腦。  
  
 您必須有 PeopleSoft 電腦的存取權，因為您必須設定環境變數 CLASSPATH (或設定資訊**傳輸屬性**螢幕) 以指向 PeopleSoft 的`PSJOA/psjoa.jar`檔案。  
  
## <a name="see-also"></a>另請參閱  
 [使用者入門](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   
 [規劃與架構](../core/planning-and-architecture13.md)