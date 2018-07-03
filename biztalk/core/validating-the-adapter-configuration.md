---
title: 驗證配接器組態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8eeb8742-7083-462b-8d3a-e58103112542
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d7fa3af1fa0116f859f0d3f39f2235be38cbc0d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008127"
---
# <a name="validating-the-adapter-configuration"></a>驗證配接器組態
同時新增接收位置和傳送埠，您必須設定您的自訂屬性中**\<**<em>配接器名稱</em> **\>傳輸屬性**  對話方塊。 AdapterHarness 專案中的 XSD 結構描述檔案會定義這些屬性。  
  
 組態結構描述的驗證發生在以下三個部分中：  
  
1.  當顯示儲存的組態時，配接器架構會先針對此結構描述來驗證儲存的 XML 文件，然後此文件才會載入到屬性頁。 此架構假設非有效的文件表示組態結構描述定義中有變更。 只有有效的文件才會載入到屬性頁。  
  
2.  當儲存組態時，如果配接器會實作**IAdapterConfigValidation**介面，架構會傳遞至建構的 XML 文件的配接器從序列化屬性頁資料。 然後，此配接器會處理該文件。 任何錯誤都應該會產生此架構所攔截並顯示給使用者的例外狀況。 任何遺漏或產生的值都應該在驗證期間產生。 使用\<瀏覽 show ="false"\>裝飾會隱藏顯示項目在屬性方格中，即使值會出現在 XML 執行個體。  
  
3.  將該值放到資料庫之前儲存組態時，此架構會再次針對此結構描述來驗證此 XML 文件。 如此可確保只會保存有效的資料。  
  
## <a name="see-also"></a>另請參閱  
 [配接器設計問題](../core/adapter-design-issues.md)