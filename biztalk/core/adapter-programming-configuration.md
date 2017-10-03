---
title: "配接器程式設計組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e5fef6c-6928-42e7-9a1f-42b5bd769937
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e908b3ac79970b917e1e7964868b3b9d5bd852d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-programming-configuration"></a>配接器程式設計組態
每個密碼同步配接器類型都有不同的組態需求，取決於您將配接器設計用於何種非 Windows 系統而定。 像分支機構應用程式，您可以使用企業單一登入的組態存放區來集中及更安全地儲存組態屬性。  
  
 如同其他組態存放區應用程式，系統管理員可以使用「企業單一登入」管理使用者介面，找出並讀取描述配接器之組態屬性的 XML 檔案。 管理工具利用 XML 檔案顯示屬性頁，為指定的配接器收集所需的屬性值。 您也可以使用 ISSOConfigStore 將 XML 名稱/值組合載入到組態存放區或從其中讀取，或者您可以使用 SSOPS 工具。  
  
 您也可以使用「企業單一登入」管理工具以啟用和停用配接器。 在初始建立時，配接器為停用。  
  
## <a name="see-also"></a>另請參閱  
 [密碼同步配接器](../core/password-sync-adapters.md)