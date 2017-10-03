---
title: "保留一般檔案組合器管線元件中的分隔符號 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adc27561-9996-49a9-b715-e313b9148506
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9d10879adfbe0ca0c68376faa48d9976fc19599
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="retaining-delimiters-in-the-flat-file-assembler-pipeline-component"></a><span data-ttu-id="8f072-102">在一般檔案組合器管線元件中保留分隔符號</span><span class="sxs-lookup"><span data-stu-id="8f072-102">Retaining Delimiters in the Flat File Assembler Pipeline Component</span></span>
<span data-ttu-id="8f072-103">如果在通過使用一般檔案組合器之自訂管線的訊息中有遺失的記錄，則一般檔案輸出中不一定會出現這些記錄的分隔符號，這要取決於這些記錄在輸入檔案中的遺失位置而定。</span><span class="sxs-lookup"><span data-stu-id="8f072-103">If there are missing records in the message going through a custom pipeline that uses the Flat File Assembler, the delimiter for those records may or may not appear in the flat file output depending on where in the input file the records are missing.</span></span>  
  
 <span data-ttu-id="8f072-104">為了確保一般檔案會保留某些分隔符號，您可以使用對應和自訂指令碼，以確定當訊息中沒有特定的輸入記錄存在時，會建立「空的」記錄。</span><span class="sxs-lookup"><span data-stu-id="8f072-104">To ensure that the flat file retain certain delimiters, you can use a map and a custom script to make sure an "empty" record is created when a specific input record does not exist in the message.</span></span> <span data-ttu-id="8f072-105">為了要讓這樣的處理方式可行，您必須確保一般檔案組合器之文件結構描述中可能是空的節點有設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="8f072-105">For this to work, you must make sure that the potentially empty nodes in the document schema for the Flat File Assembler have the following properties set as shown:</span></span>  
  
|<span data-ttu-id="8f072-106">屬性</span><span class="sxs-lookup"><span data-stu-id="8f072-106">Property</span></span>|<span data-ttu-id="8f072-107">設定</span><span class="sxs-lookup"><span data-stu-id="8f072-107">Setting</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="8f072-108">保留空白資料的分隔符號</span><span class="sxs-lookup"><span data-stu-id="8f072-108">Preserve Delimiter for Empty Data</span></span>|<span data-ttu-id="8f072-109">是</span><span class="sxs-lookup"><span data-stu-id="8f072-109">Yes</span></span>|  
|<span data-ttu-id="8f072-110">隱藏尾端分隔符號</span><span class="sxs-lookup"><span data-stu-id="8f072-110">Suppress Trailing Delimiters</span></span>|<span data-ttu-id="8f072-111">否</span><span class="sxs-lookup"><span data-stu-id="8f072-111">No</span></span>|  
|<span data-ttu-id="8f072-112">產生空節點 (在根節點上設定)</span><span class="sxs-lookup"><span data-stu-id="8f072-112">Generate Empty Nodes (set this on the root node)</span></span>|<span data-ttu-id="8f072-113">True</span><span class="sxs-lookup"><span data-stu-id="8f072-113">True</span></span>|  
  
### <a name="to-create-a-map-that-creates-an-empty-record"></a><span data-ttu-id="8f072-114">若要建立會建立空記錄的對應</span><span class="sxs-lookup"><span data-stu-id="8f072-114">To create a map that creates an "empty" record</span></span>  
  
1.  <span data-ttu-id="8f072-115">將新的對應加入到 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="8f072-115">Add a new map to your BizTalk project.</span></span>  
  
2.  <span data-ttu-id="8f072-116">將一般檔案組合器使用的文件結構描述指定為對應來源和對應目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="8f072-116">Specify the document schema used by the Flat File Assembler as both the map source and map destination schema.</span></span>  
  
3.  <span data-ttu-id="8f072-117">將不是空的來源欄位對應到相對應的目的欄位。</span><span class="sxs-lookup"><span data-stu-id="8f072-117">Map the source fields that will not be empty to the corresponding destination fields.</span></span>  
  
4.  <span data-ttu-id="8f072-118">如果是那些可能是空的欄位，請使用自訂指令碼來檢查來源欄位是不是空的，然後傳回空字串 (而不是 Nil)。</span><span class="sxs-lookup"><span data-stu-id="8f072-118">For those fields that may be empty, use a custom script to check if the source field is empty and return an empty string (instead of Nil).</span></span> <span data-ttu-id="8f072-119">請使用類似以下的指令碼：</span><span class="sxs-lookup"><span data-stu-id="8f072-119">Use a script like the following:</span></span>  
  
    ```  
    public string ValOrEmpty(string val)  
    {  
         return (val.Length > 0) ? val : "";  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8f072-120">您必須針對每一個可能是空的對應欄位建立具有唯一函式名稱的指令碼。</span><span class="sxs-lookup"><span data-stu-id="8f072-120">You must create a script with a unique function name for each potentially empty field you map.</span></span> <span data-ttu-id="8f072-121">例如，如果有三個欄位可能是空的，您可能會有名為 `ValOrEmpty1`、`ValOrEmpty2`、`ValOrEmpty3` 的函式。</span><span class="sxs-lookup"><span data-stu-id="8f072-121">For example, if you have three fields that may be empty, you might have functions named `ValOrEmpty1`, `ValOrEmpty2`, `ValOrEmpty3`.</span></span>  
  
5.  <span data-ttu-id="8f072-122">使用 BizTalk Server 管理主控台來設定具有自訂管線的傳送埠以及一般檔案組合器元件，將此對應當做輸出對應來使用。</span><span class="sxs-lookup"><span data-stu-id="8f072-122">Using BizTalk Server Administration console, configure the send port with the custom pipeline and flat file assembler component to use the map as an outbound map.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f072-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f072-123">See Also</span></span>  
 <span data-ttu-id="8f072-124">[如何設定傳送埠的輸出對應](../core/how-to-configure-outbound-maps-for-a-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="8f072-124">[How to Configure Outbound Maps for a Send Port](../core/how-to-configure-outbound-maps-for-a-send-port.md) </span></span>  
 [<span data-ttu-id="8f072-125">一般檔案組合器管線元件</span><span class="sxs-lookup"><span data-stu-id="8f072-125">Flat File Assembler Pipeline Component</span></span>](../core/flat-file-assembler-pipeline-component.md)