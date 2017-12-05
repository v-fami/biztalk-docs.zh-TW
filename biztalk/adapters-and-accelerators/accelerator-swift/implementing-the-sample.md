---
title: "實作範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd788fd3-b070-40d5-a3d3-ac8e5208cc47
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6622d201c6f7b7d94694a77198d0eb562482489
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="implementing-the-sample"></a><span data-ttu-id="c9d56-102">實作範例</span><span class="sxs-lookup"><span data-stu-id="c9d56-102">Implementing the Sample</span></span>
<span data-ttu-id="c9d56-103">若要實作的範例，請繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c9d56-103">To implement the sample, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="c9d56-104">建立新的資料夾 for SWIFT 結構描述 (\<DocumentSchemaLocation\>公用程式語法中)。</span><span class="sxs-lookup"><span data-stu-id="c9d56-104">Create a new folder for SWIFT schemas (\<DocumentSchemaLocation\> in the utility syntax).</span></span> <span data-ttu-id="c9d56-105">您即將建立/修改 InfoPath 表單的所有結構描述必須位於此資料夾中，當您執行此公用程式。</span><span class="sxs-lookup"><span data-stu-id="c9d56-105">All schemas for which you are going to create/modify the InfoPath forms must be located in this folder when you execute the utility.</span></span>  
  
2.  <span data-ttu-id="c9d56-106">如果產生的 InfoPath 表單 MT 訊息然後複製**SWIFT 基底 Types.xsd**和**SWIFT 常見資料 Types.xsd**從**\<磁碟機：\> files\Microsoft BizTalk Accelerator for SWIFT\<訊息組件版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<訊息組件版本\>\Base 結構描述**到資料夾，您建立 SWIFT 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c9d56-106">If you are generating InfoPath forms for MT messages then copy **SWIFT Base Types.xsd** and **SWIFT Common Data Types.xsd** from **\<drive :\> \Program Files\Microsoft BizTalk Accelerator for SWIFT \<Message Pack Version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<Message Pack Version\>\Base Schemas** into the folder that you created for SWIFT schemas.</span></span>  
  
3.  <span data-ttu-id="c9d56-107">複製您要建立放在您為 SWIFT 的結構描述在步驟 1 中建立資料夾的 InfoPath 表單的所有結構描述。</span><span class="sxs-lookup"><span data-stu-id="c9d56-107">Copy all schemas for which you are going to create InfoPath forms into the folder that you created for SWIFT schemas in Step 1.</span></span>  
  
4.  <span data-ttu-id="c9d56-108">建立或指定要保留建立的 InfoPath 表單範本方案檔的資料夾 (\<DestinationFolderPath\>公用程式語法中)。</span><span class="sxs-lookup"><span data-stu-id="c9d56-108">Create or designate a folder to hold the created InfoPath form template solution files (\<DestinationFolderPath\> in the utility syntax).</span></span> <span data-ttu-id="c9d56-109">如果您未建立輸出資料夾，此公用程式會建立相同路徑和您在命令列傳遞的名稱。</span><span class="sxs-lookup"><span data-stu-id="c9d56-109">If you do not create the output folder, the utility will create the same with path and name that you pass on the command line.</span></span>  
  
5.  <span data-ttu-id="c9d56-110">[選用]-建立文字檔\<NameOfFileContainingSchemaList\>其中列出要產生 InfoPath 表單的訊息的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="c9d56-110">[Optional]-  Create a text file \<NameOfFileContainingSchemaList\> that lists the message types for messages for which the InfoPath form is to be generated.</span></span> <span data-ttu-id="c9d56-111">例如： 訊息類型可以是 MT103，MT102 等等。透過命令列，而不是建立此文字檔案時，可以直接傳遞訊息名稱。</span><span class="sxs-lookup"><span data-stu-id="c9d56-111">For e.g. Message Type can be MT103, MT102 etc. The Message names can directly be passed through the command line instead of creating this text file.</span></span>  
  
## <a name="syntax-of-command-usage-for-formgeneratorexe"></a><span data-ttu-id="c9d56-112">FormGenerator.exe 的命令使用方式的語法</span><span class="sxs-lookup"><span data-stu-id="c9d56-112">Syntax of Command usage for FormGenerator.exe</span></span>  
  
```csharp  
FormGenerator [-b]   [-#] <TemplateFolderPath> [<TemplateFolderPath2>   
   [...<TemplateFolderPath#>]]  
 <DestinationFolderPath>     <DocumentSchemaLocation>  
   { [<SpaceSeparatedDocumentSchemaList>] |   [-f <NameOfFileContainingSchemaList>] }  
  
```  
  
 <span data-ttu-id="c9d56-113">其中：</span><span class="sxs-lookup"><span data-stu-id="c9d56-113">Where:</span></span>  
  
-   <span data-ttu-id="c9d56-114">-b： 如果指定，會在建立後編譯表單。</span><span class="sxs-lookup"><span data-stu-id="c9d56-114">-b: If specified, forms will be compiled after creation.</span></span>  
  
-   <span data-ttu-id="c9d56-115">TemplateFolderPath： 包含用於建立 InfoPath 解決方案範本檔案的資料夾</span><span class="sxs-lookup"><span data-stu-id="c9d56-115">TemplateFolderPath: the folder containing the template files used to create the InfoPath solution</span></span>  
  
-   <span data-ttu-id="c9d56-116">-#: 如果指定，範本會查閱中多個範本的路徑 (最大數量整數形式指定數字 #) 和指定的順序。</span><span class="sxs-lookup"><span data-stu-id="c9d56-116">-#: If specified, templates will be looked up in multiple template paths (as many as the integer number # specifies) and in the order specified.</span></span>  
  
-   <span data-ttu-id="c9d56-117">DestinationFolderPath: 資料夾將會建立表單</span><span class="sxs-lookup"><span data-stu-id="c9d56-117">DestinationFolderPath: the folder where the forms will be created</span></span>  
  
-   <span data-ttu-id="c9d56-118">結構描述 （包括基底序號和一般 MT 訊息的結構描述） 的 DocumentSchemaLocation： 位置</span><span class="sxs-lookup"><span data-stu-id="c9d56-118">DocumentSchemaLocation: location of schemas (including base and common schemas for MT messages)</span></span>  
  
-   <span data-ttu-id="c9d56-119">SpaceSeparatedDocumentSchemaList： 以空格分隔的清單 MT103 MT300 類似的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c9d56-119">SpaceSeparatedDocumentSchemaList: space-separated list of schemas like MT103 MT300.</span></span>  
  
-   <span data-ttu-id="c9d56-120">-f： 如果指定，必須從檔案讀取結構描述清單。</span><span class="sxs-lookup"><span data-stu-id="c9d56-120">-f: If specified, the schema list needs to be read from a file.</span></span>  
  
-   <span data-ttu-id="c9d56-121">NameOfFileContainingSchemaList： 包含清單的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c9d56-121">NameOfFileContainingSchemaList: name of file containing the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c9d56-122">上述命令是 MT、 MX 和類別 0 的一般命令訊息。</span><span class="sxs-lookup"><span data-stu-id="c9d56-122">The above command is a generic command for MT, MX and Category 0 messages.</span></span> <span data-ttu-id="c9d56-123">產生這些表單類型的特定命令列在下面各節。</span><span class="sxs-lookup"><span data-stu-id="c9d56-123">Specific commands to generate these types of forms are given in the below sections.</span></span>