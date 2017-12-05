---
title: "配接器架構組態結構描述裝飾標記 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d5d7f6b-2273-45a6-ba9d-43201760cf22
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d49aac9f11ef48bd0a66dcc9bda3a769cd6c34f4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="adapter-framework-configuration-schema-decoration-tags"></a>配接器架構組態結構描述裝飾標記
您可以使用在此主題中描述，組態結構描述檔案內的標記，來顯示和組織配接器屬性頁上的資料。  
  
 下圖顯示 FTP 接收位置屬性頁如何實作這些標記中的一些標記。  
  
 ![](../core/media/ebiz-prog-custad-tags.gif "ebiz_prog_custad_tags")  
\<描述\>， \<displayname\>，和\<類別\>FTP 配接器屬性頁中的標籤  
  
## <a name="designer"></a>\<設計工具\>  
 BizTalk 配接器架構會裝飾出現之間\<baf: designer\>標記和\</baf:designer\>結束標記。 \<Baf: designer\>標記可協助區分配接器架構\<appinfo\>和其他配接器提供\<appinfo\>資訊。  
  
## <a name="category"></a>\<類別目錄\>  
 \<類別\>裝飾包含用來分隔在屬性方格中的項目分組的字串。 此裝飾會將具有相同類別字串的所有項目都顯示為該類別的部屬項目。  
  
 您可以當地語系化\<類別\>項目。  
  
## <a name="description"></a>\<描述\>  
 \<描述\>裝飾包含用來在屬性方格的底端的項目提供描述性文字的字串。  
  
 您可以當地語系化\<描述\>項目。  
  
## <a name="displayname"></a>\<顯示名稱\>  
 \<Displayname\>裝飾包含用來顯示的項目名稱的字串。 這可讓您使用空格、 片語，依此類推，不會允許針對時\<元素\>或\<屬性\>名稱。  
  
 您可以當地語系化\<displayname\>項目。  
  
## <a name="readonly"></a>\<readonly\>  
 \<Fixed =""\>裝飾可控制是否可編輯欄位。 `true` 的 "fixed" 屬性值 (預設值) 會使欄位變成唯讀。  
  
 當實作外部編輯器時，實作外部**TypeConverter**類別並覆寫**getstandardvaluesexclusive （itypedescriptorcontext)**方法改為。 傳回 `true` 會使欄位變成唯讀，不過卻會保留對自訂編輯器的存取。  
  
## <a name="browsable"></a>\<可瀏覽\>  
 \<可瀏覽顯示 =""\>裝飾可控制是否在屬性方格中顯示的欄位。 `True` 的 "show" 屬性值 (預設值) 會使欄位出現在方格中。  
  
## <a name="converter"></a>\<轉換程式\>  
 \<轉換器組件 =""\>裝飾指定所要**TypeConverter**類別名稱\<元素\>或\<屬性\>。 選擇性的"assembly"屬性值指定包含所需的組件的路徑**TypeConverter**。 當沒有指定 "assembly" 值時，類別名稱必須包含全域組件快取的組件名稱、索引鍵、文化特性和版本值。  
  
## <a name="editor"></a>\<編輯器\>  
 \<編輯器組件 =""\>裝飾指定所要**UITypeEditor**類別名稱\<元素\>或\<屬性\>。 選擇性的"assembly"屬性值指定包含所需的組件的路徑**UITypeEditor**。 當沒有指定 "assembly" 值時，類別名稱必須包含全域組件快取的組件名稱、索引鍵、文化特性和版本值。  
  
## <a name="null-values-for-optional-enumerations"></a>選擇性列舉的 Null 值  
 當使用選擇性的列舉，其中一個值應該是\<無\>來表示 null 值。 這不是內建的標記，不過如果列舉衍生自 xsd:string，即可提供被視為「無」的列舉值以達成這點。 這對衍生自 xsd:int 的列舉則是不可能的，因為整數都必須保留值。  
  
## <a name="see-also"></a>請參閱  
 [配接器架構設定結構描述延伸模組](../core/adapter-framework-configuration-schema-extensions.md)