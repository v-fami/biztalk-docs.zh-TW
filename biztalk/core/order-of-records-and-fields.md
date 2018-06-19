---
title: 記錄和欄位的順序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Mapper, sorting
- XSLT, sorting
ms.assetid: 7fa9b5cd-73bc-496f-a081-4a45da3afe42
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5826d46fef73400a5d54e2d1154a1647af85294e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263854"
---
# <a name="order-of-records-and-fields"></a>記錄和欄位的順序
BizTalk 對應工具所使用的「可延伸樣式表語言轉換」(XSLT) 並不保證輸出項目和屬性的輸出順序。 這是因為 BizTalk 對應工具透過檢查目的結構描述之結構，然後經由格線頁將項目傳回，從來源結構描述的結構擷取值以產生 XSLT。 例如，若您要建立一個輸出檔案，將 BillTo Address 記錄列在 ShipTo Address 記錄之前，您必須確保在目的結構描述中，BillTo Address 位在 ShipTo Address 記錄之前。  
  
> [!IMPORTANT]
>  項目和屬性出現在輸出執行個體訊息中的順序相依於記錄和欄位在對應的目的結構描述中的順序。  
  
## <a name="see-also"></a>另請參閱  
 [對應](../core/maps.md)   
 [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)