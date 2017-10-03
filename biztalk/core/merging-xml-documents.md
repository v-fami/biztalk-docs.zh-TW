---
title: "合併 XML 文件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML, documents
- process management solution tutorial, merging XML documents
ms.assetid: 444c983a-397a-4342-85e1-80bb152986d9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94684cd9bf1992a592efd7b97c46838c9c9a3134
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="merging-xml-documents"></a>合併 XML 文件
其中一個訊息， **OrderBroker**協調流程會建立一個 SQL Server 歷程記錄資料庫更新。 此訊息包含來自訂單訊息的欄位，以及原始訂單訊息。 原始訂單會在此訊息中以字串顯示。 這符合資料庫中訂單歷程記錄的資料型別。  
  
 取得訊息、將它轉換為字串，並利用對應將它放置於另一個訊息中，是不可能做到的。 協調流程會使用 helper 函式， **InsertOrderBody**，若要將原始訂單訊息為字串加入至基底歷程記錄訊息。  
  
 **OrderBroker**協調流程會使用對應， **CSR_OrderRequest_To_SQLHistoryInsert**，以將訂單訊息轉換成基底歷程記錄訊息。 訂單的資訊會顯示為屬性**OrderLog**項目。 原始訊息則會顯示為此項目的另一個屬性。  
  
 **InsertOrderBody**方法做為引數，會採用原始訂單訊息、 基底歷程記錄訊息，並傳回完成的歷程記錄訊息。 下列程式碼會顯示將訊息當成字串插入之方法的一部分：  
  
```  
public static XmlDocument InsertOrderBody( XmlDocument orderDoc,   
                                    XmlDocument historyInsertDoc)  
{  
...  
    XmlNode root = historyInsertDoc.FirstChild;  
  
    //Create a new attribute.  
    XmlNode attr = historyInsertDoc.CreateNode(XmlNodeType.Attribute,  
                                     "OriginalMsg", root.NamespaceURI);  
    attr.Value = orderDoc.OuterXml;  
  
    try  
    {  
        // XPath expression not shown for formatting reasons and  
        // replaces ".." in the following code  
        XmlNode destnode = historyInsertDoc.SelectSingleNode("..");  
        //Add the attribute to the document.  
        destnode.Attributes.SetNamedItem(attr);  
    }  
...  
  
    return historyInsertDoc;  
}  
```  
  
 在確認收到兩個引數之後, **InsertOrderBody**方法會尋找歷程記錄更新訊息的根節點。 然後它會建立一個節點，其中包含**OriginalMsg**屬性，並將原始訂單訊息指派給屬性的值。 此時，節點只是存在而已。 還不是項目的一部分。  
  
 在建立屬性節點之後，此方法會尋找將使用 XPath 運算式來附加屬性的節點。 找到該節點之後，此方法會將屬性節點加入至該節點的屬性集合中。  
  
> [!NOTE]
>  雖然**OriginalMsg**屬性一開始沒有基底歷程記錄訊息中，它是，當然，結構描述中指定。 在程式碼中加入至訊息的 XML 項目，應該在那些訊息的結構描述中予以指定。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md)