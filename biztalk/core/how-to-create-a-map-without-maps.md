---
title: "如何建立不含對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 520ec44f-5aca-4271-8835-b8e784214061
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81be2591c1d8f20f5b8dd01cf01c03e8daed9c9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-map-without-maps"></a>如何建立不含對應的對應
若您擁有已經用來轉換執行個體訊息的 XSLT 程式碼，則可直接使用該程式碼而不需建立對應。  
  
 使用您的 XSLT 程式碼包含建立空的對應，並設定其**自訂 XSLT 路徑**格線屬性。 如果您的 XSLT 程式碼使用外部.NET 組件，您也需要建立自訂延伸模組 XML 檔案。 自訂延伸模組 XML 檔案結構的相關資訊，請參閱**自訂延伸模組 XML （格線屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="use-custom-xslt-code-in-place-of-a-map"></a>使用自訂 XSLT 程式碼取代對應  
  
1.  在專案中建立空白 BizTalk 對應，並設定來源與目的結構描述。  
  
     如需建立對應及設定結構描述資訊，請參閱[建立對應](../core/creating-maps.md)。  
  
2.  在 [格線] 檢視中，按一下對應工具格線。  
  
     [屬性] 視窗會顯示**方格**屬性。  
  
3.  在 [屬性] 視窗中，選取**自訂 XSLT 路徑**按一下省略符號 (**...**) 按鈕。  
  
4.  在**開啟**對話方塊，瀏覽至檔案，然後按一下**開啟**。  
  
     **自訂 XSLT 路徑**屬性設定。  
  
> [!NOTE]
>  [BizTalk 對應工具] 僅支援 XSLT 1.0。 在 [BizTalk 對應工具] 中不支援使用 XSLT 2.0。  
  
## <a name="see-also"></a>另請參閱  
 [關於對應](../core/about-maps.md)   
 [使用內嵌 XSLT 與 XSLT 呼叫範本指令碼](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)   
 [自訂 XSLT](../core/custom-xslt.md)   