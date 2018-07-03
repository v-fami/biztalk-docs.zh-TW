---
title: 錯誤擷取程式範例類別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Error Extractor Sample class
- errors, Error Extractor Sample class
ms.assetid: d0d59b21-d80a-4466-a77a-1d3b7df1bc2a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1085af05221b252bb6942e2c32bbe1f91c8d7688
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010767"
---
# <a name="error-extractor-sample-class"></a><span data-ttu-id="49233-102">錯誤擷取程式範例類別</span><span class="sxs-lookup"><span data-stu-id="49233-102">Error Extractor Sample Class</span></span>
<span data-ttu-id="49233-103">Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]解譯器會序列化為 XML 物件，錯誤，並將 XML 物件附加至多部分訊息的錯誤區段。</span><span class="sxs-lookup"><span data-stu-id="49233-103">The Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] disassembler serializes errors to an XML object, and attaches the XML object to the error section of a multipart message.</span></span> <span data-ttu-id="49233-104">反組譯工具接著會將失敗的訊息發佈到 MessageBox 資料庫，就像一樣是有效的訊息。</span><span class="sxs-lookup"><span data-stu-id="49233-104">The disassembler then publishes the failed message to the MessageBox database just as it would a valid message.</span></span> <span data-ttu-id="49233-105">因此，無法至 MessageBox 資料庫的訊息包含錯誤詳細資料。</span><span class="sxs-lookup"><span data-stu-id="49233-105">Therefore, failed messages carry error details into the MessageBox database.</span></span> <span data-ttu-id="49233-106">您可以使用錯誤擷取程式範例類別，來擷取失敗的訊息中的錯誤詳細資料，並產生一個檔案包含錯誤詳細資料和另一個具有原始訊息的檔案。</span><span class="sxs-lookup"><span data-stu-id="49233-106">You can use the Error Extractor Sample Class to extract the error details from a failed message, and generate one file that has the error details and another file that has the original message.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="49233-107">錯誤擷取程式範例類別是在 SDK 中的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="49233-107">The Error Extractor Sample Class is sample code in the SDK.</span></span> <span data-ttu-id="49233-108">它並不適用於實際執行時使用。</span><span class="sxs-lookup"><span data-stu-id="49233-108">It is not intended for use in production.</span></span>  
  
 <span data-ttu-id="49233-109">若要使用錯誤擷取程式範例類別，您必須建立協調流程以處理失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="49233-109">To use the Error Extractor Sample Class, you must create an orchestration to process the failed message.</span></span> <span data-ttu-id="49233-110">此協調流程包括失敗訊息的主體擷取、 擷取錯誤訊息的一部分失敗，並接著撰寫本文及到不同的 XML 檔案的錯誤部分的步驟。</span><span class="sxs-lookup"><span data-stu-id="49233-110">This orchestration includes steps to extract the body of the failed message, extract the error part of the failed message, and then write the body and the error part to separate XML files.</span></span> <span data-ttu-id="49233-111">協調流程會代表每個步驟中 「 運算式 」 階段錯誤擷取程式範例類別中呼叫一或多個下列方法：</span><span class="sxs-lookup"><span data-stu-id="49233-111">The orchestration represents each of these steps in an expression stage that calls one or more of the following methods in the Error Extractor Sample Class:</span></span>  
  
## <a name="getbodypartasstring-method"></a><span data-ttu-id="49233-112">GetBodyPartAsString 方法</span><span class="sxs-lookup"><span data-stu-id="49233-112">GetBodyPartAsString method</span></span>  
 <span data-ttu-id="49233-113">這個方法會傳回字串，包含的 XML 位於訊息內文部分 XLANG 'xml'。</span><span class="sxs-lookup"><span data-stu-id="49233-113">This method returns a string that contains the XML found in the body part of the XLANG message 'xm'.</span></span> <span data-ttu-id="49233-114">方法應包含的內文部分 XLANG 訊息 'xml' 呼叫 「 BodySegment。 」</span><span class="sxs-lookup"><span data-stu-id="49233-114">The method expects the XLANG message 'xm' to contain a body part called "BodySegment."</span></span> <span data-ttu-id="49233-115">因此，您必須宣告 'xml' 中呼叫的協調流程，使用此內文部分名稱。</span><span class="sxs-lookup"><span data-stu-id="49233-115">Therefore, you must declare 'xm' in the calling orchestration with this body part name.</span></span> <span data-ttu-id="49233-116">如果 「 BodySegment"不存在 'xml'，過程**GetBodyPartAsString**會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="49233-116">If "BodySegment" does not exist as a part of 'xm', **GetBodyPartAsString** throws an exception.</span></span>  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetBodyPartAsString(XLANGMessage xm);  
```  
  
## <a name="geterrorpartasstring-method"></a><span data-ttu-id="49233-117">GetErrorPartAsString 方法</span><span class="sxs-lookup"><span data-stu-id="49233-117">GetErrorPartAsString method</span></span>  
 <span data-ttu-id="49233-118">這個方法會傳回字串，包含的 XML 位於錯誤的 XLANG 訊息部分 'xml'。</span><span class="sxs-lookup"><span data-stu-id="49233-118">This method returns a string that contains the XML found in the error part of the XLANG message 'xm'.</span></span> <span data-ttu-id="49233-119">方法應包含錯誤部分 XLANG 訊息 'xml' 呼叫 「 ErrorSegment。 」</span><span class="sxs-lookup"><span data-stu-id="49233-119">The method expects the XLANG message 'xm' to contain an error part called "ErrorSegment."</span></span> <span data-ttu-id="49233-120">因此，您必須宣告 'xml' 中呼叫的協調流程，此錯誤的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="49233-120">Therefore, you must declare 'xm' in the calling orchestration with this error part name.</span></span> <span data-ttu-id="49233-121">如果 「 ErrorSegment"不存在 'xml'，過程**GetErrorPartAsString**會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="49233-121">If "ErrorSegment" does not exist as a part of 'xm', **GetErrorPartAsString** throws an exception.</span></span>  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetErrorPartAsString(XLANGMessage xm);  
```  
  
## <a name="writetofile-method"></a><span data-ttu-id="49233-122">WriteToFile 方法</span><span class="sxs-lookup"><span data-stu-id="49233-122">WriteToFile method</span></span>  
 <span data-ttu-id="49233-123">這個方法會寫入的字串*訊息*參數所指定的檔案*filePath*參數。</span><span class="sxs-lookup"><span data-stu-id="49233-123">This method writes the string from the *message* parameter to the file specified by the *filePath* parameter.</span></span>  
  
```  
SWIFTErrorExtractor.ErrorExtractor.WriteToFile(string filePath, string message);  
```  
  
 <span data-ttu-id="49233-124">A4SWIFT 安裝程式安裝錯誤擷取程式範例類別 (SWIFTErrorExtractor.dll) 在 A4SWIFT SDK 的一部分\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial\SWIFTErrorExtractor。</span><span class="sxs-lookup"><span data-stu-id="49233-124">A4SWIFT Setup installs the Error Extractor Sample Class (SWIFTErrorExtractor.dll) as part of the A4SWIFT SDK in \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial\SWIFTErrorExtractor.</span></span> <span data-ttu-id="49233-125">此資料夾也包含範例類別 (ErrorExtractor.cs) 的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="49233-125">This folder also includes the source code for the sample class (ErrorExtractor.cs).</span></span>  
  
 <span data-ttu-id="49233-126">若要從協調流程呼叫 SWIFTErrorExtractor.dll，您必須發行至全域組件快取的.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="49233-126">To call SWIFTErrorExtractor.dll from the orchestration, you must publish the .dll file to the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49233-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49233-127">See Also</span></span>  
 [<span data-ttu-id="49233-128">工具</span><span class="sxs-lookup"><span data-stu-id="49233-128">Tools</span></span>](../../adapters-and-accelerators/accelerator-swift/tools.md)