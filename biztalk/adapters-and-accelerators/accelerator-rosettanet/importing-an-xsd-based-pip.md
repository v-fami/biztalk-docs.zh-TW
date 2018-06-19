---
title: 匯入以 XSD 為基礎的 PIP |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PIPs, importing
- XSD-based PIPs
- PIPs, XSD-based PIPs
ms.assetid: d12441d4-79bf-4c24-9360-4b78c1da0d34
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d8865d7a75bdb06895b963b8269ed457cd5804f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961652"
---
# <a name="importing-an-xsd-based-pip"></a><span data-ttu-id="0651d-102">匯入以 XSD 為基礎的 PIP</span><span class="sxs-lookup"><span data-stu-id="0651d-102">Importing an XSD-based PIP</span></span>
<span data-ttu-id="0651d-103">雖然由 RosettaNet.org 提供的 PIP 大部分是以 DTD 為基礎，但較新的 PIP 則是以 XSD 為基礎。</span><span class="sxs-lookup"><span data-stu-id="0651d-103">While the majority of PIPS provided by RosettaNet.org are DTD-based, newer PIPS are XSD-based.</span></span> <span data-ttu-id="0651d-104">下列程序說明如何匯入以 XSD 為基礎的 PIP。</span><span class="sxs-lookup"><span data-stu-id="0651d-104">The following procedure describes how to import XSD-based PIPS.</span></span>  
  
### <a name="to-import-an-xsd-based-pip"></a><span data-ttu-id="0651d-105">匯入以 XSD 為基礎的 PIP</span><span class="sxs-lookup"><span data-stu-id="0651d-105">To import an XSD-based PIP</span></span>  
  
1.  <span data-ttu-id="0651d-106">從 RosettaNet.org 在下載以 XSD 為基礎的 PIP.zip 檔案[http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859)或從 CIDX.org 在[http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361)。</span><span class="sxs-lookup"><span data-stu-id="0651d-106">Download the XSD-based PIP .zip file from RosettaNet.org at [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859) or from CIDX.org at [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361).</span></span> <span data-ttu-id="0651d-107">從 .zip 檔解壓縮這些檔案。</span><span class="sxs-lookup"><span data-stu-id="0651d-107">Extract the files from the .zip file.</span></span> <span data-ttu-id="0651d-108">您需要的檔案是放在 [XML] 資料夾的子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0651d-108">The files that you need will be in the subfolders of the XML folder.</span></span>  
  
2.  <span data-ttu-id="0651d-109">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0651d-109">Open Visual Studio.</span></span> <span data-ttu-id="0651d-110">建立新的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="0651d-110">Create a new BizTalk project.</span></span>  
  
3.  <span data-ttu-id="0651d-111">開啟 [Windows 檔案總管]，移至在步驟 1 所解壓縮的 XML 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0651d-111">Open Windows Explorer, and move to the XML folder extracted in step 1.</span></span> <span data-ttu-id="0651d-112">選取 XML 資料夾下的第一個資料夾，將它拖曳到 Visual Studio 的 [方案總管] 中，並且放置在您的專案中。</span><span class="sxs-lookup"><span data-stu-id="0651d-112">Select the first folder under the XML folder, drag it to Solutions Explorer in Visual Studio, and drop it into your project.</span></span> <span data-ttu-id="0651d-113">對 [XML] 資料夾中的每一個子資料夾重複上述動作，在您的專案中建立相同的資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="0651d-113">Repeat for each of the subfolders in the XML folder, creating the same folder structure in your project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0651d-114">對於 PIP7c7 PIP，這些資料夾會包括 [Domain]、[Interchange]、[System] 和 [Universal] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0651d-114">For a PIP7c7 PIP these folders would include the Domain, Interchange, System, and Universal folders.</span></span> <span data-ttu-id="0651d-115">對於這個 PIP，您的專案應該包含 [Domain]、[Interchange]、[System] 和 [Universal] 資料夾及其內容。</span><span class="sxs-lookup"><span data-stu-id="0651d-115">For this PIP, your project should contain Domain, Interchange, System, and Universal folders and their contents.</span></span>  
  
4.  <span data-ttu-id="0651d-116">如果在 [System] 資料夾中有 .xsd 檔案，請在 [方案總管] 中選取它，並且變更屬性頁面中所列的命名空間，使它不包含字串 ".System"。</span><span class="sxs-lookup"><span data-stu-id="0651d-116">If there is an .xsd file in the System folder, select it in Solution Explorer and change the namespace listed in the property page so that it does not contain the string ".System".</span></span> <span data-ttu-id="0651d-117">例如，對於 PIP7c7 PIP，您可以將命名空間變更為 "PIP7c7._System"。</span><span class="sxs-lookup"><span data-stu-id="0651d-117">For example, for PIP7c7 PIP, you could change the namespace to be "PIP7c7._System".</span></span> <span data-ttu-id="0651d-118">對 [System] 資料夾中的每一個 .xsd 檔案重複上述動作。</span><span class="sxs-lookup"><span data-stu-id="0651d-118">Repeat for each .xsd file in the System folder.</span></span> <span data-ttu-id="0651d-119">如果您不變更命名空間，您將會看到類似下列的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="0651d-119">If you do not change the namespace, you will receive the following or a similar error:</span></span>  
  
    ```  
    The type or namespace name 'SerializableAttribute' does not exist in the class or namespace 'PIP7C7.System'.  
    ```  
  
5.  <span data-ttu-id="0651d-120">檢閱所有.xsd 檔案，請確認\<結構描述\>TypeName 和根節點 TypeName 不相同。</span><span class="sxs-lookup"><span data-stu-id="0651d-120">Review all .xsd files to ensure that the \<schema\> TypeName and root node TypeName are not identical.</span></span> <span data-ttu-id="0651d-121">例如，對於 PIP7C7 PIP PartnerIdentification.xsd Universal 資料夾中的有 'PartnerIdentification' 的 TypeName 兩個\<結構描述\>（當在方案總管 中選取 PartnerIdentification.xsd） 以及PartnerIdentification 根節點。</span><span class="sxs-lookup"><span data-stu-id="0651d-121">For example, for a PIP7C7 PIP the PartnerIdentification.xsd in the Universal folder has the TypeName of 'PartnerIdentification' for both the \<schema\> (when PartnerIdentification.xsd is selected in Solution Explorer) and also the PartnerIdentification root node.</span></span> <span data-ttu-id="0651d-122">若要更正這種情況，請在 [方案總管] 中選取 PartnerIdentification.xsd，然後變更屬性頁面中的 TypeName 屬性，使它不會包含與 PartnerIdentification 根節點相同的 TypeName。</span><span class="sxs-lookup"><span data-stu-id="0651d-122">To correct this, select PartnerIdentification.xsd in Solution Explorer, and then in the property page change the TypeName property so that it does not contain the same TypeName as the PartnerIdentification root node.</span></span> <span data-ttu-id="0651d-123">例如，將 TypeName 變更為 "_PartnerIdentification"。</span><span class="sxs-lookup"><span data-stu-id="0651d-123">For example, change the TypeName to be "_PartnerIdentification".</span></span> <span data-ttu-id="0651d-124">如果不執行這個步驟，當您嘗試建置專案時便會看到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="0651d-124">If you do not take this step, you will receive the following error when you try to build the project:</span></span>  
  
    ```  
    Node "<Schema>" - This schema file has a TypeName that collides with the RootNode TypeName of one of its root Nodes. Make sure that they are different.  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0651d-125">錯誤清單中的 [檔案] 欄位將會顯示哪些檔案發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="0651d-125">The File column in the error list will indicate which files have this problem.</span></span>  
  
6.  <span data-ttu-id="0651d-126">建置然後再部署專案。</span><span class="sxs-lookup"><span data-stu-id="0651d-126">Build and then deploy the project.</span></span>