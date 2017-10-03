---
title: "使用大型結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8348036d-6edb-46a3-badd-0223cfe0a92f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5c5ef679070009b5dfb5fdd403d238cfe243cb2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-large-schemas"></a>使用大型結構描述
當結構描述變得非常大，您可能發現重新整理 XSD 檢視的速度變慢，且使用者介面的其他方面也可能大受影響。 此問題解決方法是關閉自動重新整理功能，並改為使用手動**重新整理**XSD 檢視要定期重新整理 XSD 檢視中的連結。 逐步說明如何開啟的自動重新整理功能關閉，請參閱 < 開啟及關閉開啟自動重新整理 XSD 檢視的 「 程序中[管理 XSD 檢視](../core/how-to-manage-the-xsd-view.md)。  
  
 效能也可能變慢的大型結構描述具有多個根附加至**結構描述**節點。 設定**根參考**屬性可能會增加使用者介面中的效能。 設定**根參考**改善效能，因為編譯器會在所有根結構描述建立 C# 類別。 單一根節點表示建立較少類別。  
  
 **驗證執行個體**可能會出現在使用者介面變慢，因為會一律對驗證結構描述驗證執行個體之前。 結構描述驗證僅發生在使用者介面。 設定**根參考**屬性也可以改善使用者介面效能在此情況下。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 編輯器](../core/using-biztalk-editor.md)