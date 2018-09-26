---
title: 實作範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cd788fd3-b070-40d5-a3d3-ac8e5208cc47
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6622d201c6f7b7d94694a77198d0eb562482489
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966700"
---
# <a name="implementing-the-sample"></a>實作範例
若要實作的範例，請繼續進行，如下所示：  
  
1.  建立新的資料夾 for SWIFT 結構描述 (\<DocumentSchemaLocation\>公用程式語法中)。 您即將建立/修改 InfoPath 表單的所有結構描述必須位於此資料夾中，當您執行此公用程式。  
  
2.  如果產生的 InfoPath 表單 MT 訊息然後複製**SWIFT 基底 Types.xsd**和**SWIFT 常見資料 Types.xsd**從**\<磁碟機：\> files\Microsoft BizTalk Accelerator for SWIFT\<訊息組件版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<訊息組件版本\>\Base 結構描述**到資料夾，您建立 SWIFT 的結構描述。  
  
3.  複製您要建立放在您為 SWIFT 的結構描述在步驟 1 中建立資料夾的 InfoPath 表單的所有結構描述。  
  
4.  建立或指定要保留建立的 InfoPath 表單範本方案檔的資料夾 (\<DestinationFolderPath\>公用程式語法中)。 如果您未建立輸出資料夾，此公用程式會建立相同路徑和您在命令列傳遞的名稱。  
  
5.  [選用]-建立文字檔\<NameOfFileContainingSchemaList\>其中列出要產生 InfoPath 表單的訊息的訊息類型。 例如： 訊息類型可以是 MT103，MT102 等等。透過命令列，而不是建立此文字檔案時，可以直接傳遞訊息名稱。  
  
## <a name="syntax-of-command-usage-for-formgeneratorexe"></a>FormGenerator.exe 的命令使用方式的語法  
  
```csharp  
FormGenerator [-b]   [-#] <TemplateFolderPath> [<TemplateFolderPath2>   
   [...<TemplateFolderPath#>]]  
 <DestinationFolderPath>     <DocumentSchemaLocation>  
   { [<SpaceSeparatedDocumentSchemaList>] |   [-f <NameOfFileContainingSchemaList>] }  
  
```  
  
 其中：  
  
-   -b： 如果指定，會在建立後編譯表單。  
  
-   TemplateFolderPath： 包含用於建立 InfoPath 解決方案範本檔案的資料夾  
  
-   -#: 如果指定，範本會查閱中多個範本的路徑 (最大數量整數形式指定數字 #) 和指定的順序。  
  
-   DestinationFolderPath: 資料夾將會建立表單  
  
-   結構描述 （包括基底序號和一般 MT 訊息的結構描述） 的 DocumentSchemaLocation： 位置  
  
-   SpaceSeparatedDocumentSchemaList： 以空格分隔的清單 MT103 MT300 類似的結構描述。  
  
-   -f： 如果指定，必須從檔案讀取結構描述清單。  
  
-   NameOfFileContainingSchemaList： 包含清單的檔案名稱。  
  
    > [!NOTE]
    >  上述命令是 MT、 MX 和類別 0 的一般命令訊息。 產生這些表單類型的特定命令列在下面各節。