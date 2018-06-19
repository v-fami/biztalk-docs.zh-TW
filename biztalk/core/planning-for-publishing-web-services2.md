---
title: 發佈 Web Services2 規劃 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web services, planning
- virtual directories, updating
- BizTalk Server Web Services Publishing Wizard
ms.assetid: 69107557-48e2-4f15-ba42-9fad476a8294
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d0b9d593a3309f7b4477f2fa735f7e265b614c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264454"
---
# <a name="planning-for-publishing-web-services"></a>規劃發佈 Web 服務
您可以從您的協調流程存取 Web 服務。 您也可以使用「BizTalk Web 服務發佈精靈」來發佈 Web 服務。  
  
 下表列出在您規劃 Web 服務時應回答的一些問題。  
  
|規劃問題|建議|  
|-----------------------|--------------------|  
|您是否已經建立自己的 BizTalk Server 專案？|您必須先建立自己的 BizTalk Server 專案，才可以執行「BizTalk Web 服務發佈精靈」。|  
|您是否已經將系統啟用成執行 Web 服務？|您必須先啟用電腦上的 Web 服務，才可以執行「BizTalk Web 服務發佈精靈」。 如需將系統啟用成 Web 服務的詳細資訊，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。|  
|您是否已確認您的結構描述只包含有效的 XML 字元和項目？|Web 服務不支援中文、日文或韓文 (CJK) Unified Ideograph Extension A 等字元。 特定的 XML 結構描述 (XSD) 項目也有所限制。 如需有效的 XML 字元和支援的元素和元素的考量的詳細資訊，請參閱[考量發佈 Web 服務時](../core/considerations-when-publishing-web-services.md)。|  
|在您的 BizTalk Server 專案中，是否有任何訊息類型會使用使用者定義的 .NET 類別？|您必須安裝其中包含訊息類型在全域組件快取 (GAC) 內參考之使用者定義 .NET 類別的組件。|  
|執行您 Web 用戶端會使用提供的認證用於**WindowsUser**內容屬性？|已發行的 Web 服務使用之 Web 用戶端所提供的認證**WindowsUser**內容屬性。 「合作對象解析」會使用這個屬性。 如果您設定合作對象使用**WindowsUser**內容屬性和 Web 用戶端使用 Web 服務的認證來比對合作對象，BizTalk Server 會識別為來自對應的預先定義合作對象的訊息。 如需合作對象解析管線元件的詳細資訊，請參閱[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [發佈 Web 服務](../core/publishing-web-services.md)