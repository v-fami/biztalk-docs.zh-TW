---
title: 產生 WSDL 與 WCF LOB 配接器 SDK |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f701d78d-b3ad-4f75-b814-e5b1f1319fb9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaf5ed992864c11d360baa30f35983f0082213b3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971071"
---
# <a name="generate-wsdl-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="7573b-102">產生 WSDL 與 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="7573b-102">Generate WSDL with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="7573b-103">在開發配接器，或從 LOB 系統變更傳回的中繼資料，通常很有用，檢視 Web 服務描述語言 (WSDL) 所傳回的介面卡，以確認您的作業的中繼資料，會產生期間正確。</span><span class="sxs-lookup"><span data-stu-id="7573b-103">During development of an adapter, or when the metadata that is returned from the LOB system changes, it is often useful to view the Web Services Description Language (WSDL) that is returned from the adapter to verify that the metadata for your operations is generated correctly.</span></span> <span data-ttu-id="7573b-104">有數種方法來產生的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="7573b-104">There are several methods to generate the WSDL.</span></span> <span data-ttu-id="7573b-105">本主題提供使用 svcutil.exe，並瀏覽中繼資料搜尋控制項的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7573b-105">This topic provides information about using svcutil.exe and the Metadata Search Browse control.</span></span>  

  
## <a name="use-svcutilexe"></a><span data-ttu-id="7573b-106">使用 svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="7573b-106">Use svcutil.exe</span></span>  
 <span data-ttu-id="7573b-107">Svcutil.exe 會是命令列公用程式隨附於 Windows SDK 的 URL 和選擇性參數，會接受及傳回 WSDL。</span><span class="sxs-lookup"><span data-stu-id="7573b-107">Svcutil.exe is a command-line utility shipped with the Windows SDK that accepts a URL and optional switches, and returns WSDL.</span></span> <span data-ttu-id="7573b-108">使用 svcutil.exe 傳回的 WSDL Echo 配接器的範例如下：</span><span class="sxs-lookup"><span data-stu-id="7573b-108">The following is an example of using svcutil.exe to return the WSDL of the Echo Adapter:</span></span>  
  
 ```
 Svcutil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False” /target:metadata
 ```
  
 <span data-ttu-id="7573b-109">這會將中繼資料儲存 Microsoft.Adapters.Samples.Echov2.wsdl。</span><span class="sxs-lookup"><span data-stu-id="7573b-109">This saves the metadata as Microsoft.Adapters.Samples.Echov2.wsdl.</span></span> <span data-ttu-id="7573b-110">如果您的配接器有許多作業，您可以選擇使用以傳回所需的作業 ' op = OperationName' 做為 URI 的一部分。</span><span class="sxs-lookup"><span data-stu-id="7573b-110">If your adapter has many operations, you can choose to return only the desired operations by using ‘op=OperationName’ as part of the URI.</span></span> <span data-ttu-id="7573b-111">使用此傳回 EchoStrings 資訊的範例如下：</span><span class="sxs-lookup"><span data-stu-id="7573b-111">The following is an example of using this to return only the EchoStrings information:</span></span>  
  
```  
SvcUtil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False&op=Echo/EchoStrings” /target:metadata  
```  
  
## <a name="use-the-metadata-search-browse-control"></a><span data-ttu-id="7573b-112">使用中繼資料搜尋瀏覽控制項</span><span class="sxs-lookup"><span data-stu-id="7573b-112">Use the Metadata Search Browse Control</span></span>  
 <span data-ttu-id="7573b-113">瀏覽中繼資料搜尋控制項是 Windows 控制項中所包含的精靈中使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7573b-113">The Metadata Search Browse control is a Windows control that is used in the wizards included in [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="7573b-114">您可以將此控制項加入任何 Windows Form 專案在 Visual Studio 中，和使用它來選取您的配接器所需的作業，然後產生的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="7573b-114">You can add this control to any Windows Forms project in Visual Studio, and use it to select your adapter, the desired operations, and then generate the WSDL.</span></span>  
  
1. <span data-ttu-id="7573b-115">開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7573b-115">Open a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt.</span></span>  
  
2. <span data-ttu-id="7573b-116">在上**檔案**功能表上，選取**新增**，然後按一下**專案**。</span><span class="sxs-lookup"><span data-stu-id="7573b-116">On the **File** menu, select **New**, and then click **Project**.</span></span>  
  
3. <span data-ttu-id="7573b-117">在 **新的專案**對話方塊中，選取**Windows 應用程式**從**範本**。</span><span class="sxs-lookup"><span data-stu-id="7573b-117">In the **New Project** dialog box, select **Windows Application** from **Templates**.</span></span> <span data-ttu-id="7573b-118">輸入專案名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7573b-118">Enter a project name, and then click **OK**.</span></span>  
  
4. <span data-ttu-id="7573b-119">開啟**工具箱**，展開**通用控制項**，以滑鼠右鍵按一下**工具箱**，然後按一下**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="7573b-119">Open the **Toolbox**, expand **Common Controls**, right-click the **Toolbox**, and then click **Choose Items**.</span></span>  
  
5. <span data-ttu-id="7573b-120">在 [**選擇工具箱項目**] 對話方塊中，尋找**MetadataUserControl**上 **.NET Framework 元件**索引標籤上，選取此項目，旁邊的核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7573b-120">In the **Choose Toolbox Items** dialog box, find **MetadataUserControl** on the **.NET Framework Components** tab, select the check box beside this item, and then click **OK**.</span></span>  
  
6. <span data-ttu-id="7573b-121">從 [工具箱] 拖曳到 Form1 的 MetadataUserControl。</span><span class="sxs-lookup"><span data-stu-id="7573b-121">From the Toolbox, drag the MetadataUserControl to Form1.</span></span> <span data-ttu-id="7573b-122">您可能需要調整表單以查看整個控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="7573b-122">You may need to resize the form to see the entire control.</span></span> <span data-ttu-id="7573b-123">您應該能夠立即執行專案，並確認控制項正常運作，可讓您選取的配接器和作業。</span><span class="sxs-lookup"><span data-stu-id="7573b-123">You should be able to run the project now and verify that the control is functional, allowing you to select an adapter and operations.</span></span>  
  
7. <span data-ttu-id="7573b-124">使用這個控制項產生的 WSDL，您必須將程式碼加入您的表單來呼叫**GetWsdl**此控制項的方法。</span><span class="sxs-lookup"><span data-stu-id="7573b-124">To generate WSDL by using this control, you must add code to your form to call the **GetWsdl** method of this control.</span></span> <span data-ttu-id="7573b-125">下列範例示範如何呼叫**GetWsdl**並將資料儲存至檔案：</span><span class="sxs-lookup"><span data-stu-id="7573b-125">The following example demonstrates how to call **GetWsdl** and save the data to file:</span></span>  
  
   ```csharp  
   private void button1_Click(object sender, EventArgs e)  
   {  
      ServiceDescription sd = mdUserControl.GetWsdl();  
      FileStream myFileStream = new FileStream(tbWsdlFileName.Text, FileMode.OpenOrCreate, FileAccess.Write);  
      StreamWriter myStreamWriter = new StreamWriter(myFileStream);  
      sd.Write(myStreamWriter);  
      myStreamWriter.Flush();  
      myStreamWriter.Close();  
      MessageBox.Show("WSDL file " + tbWsdlFileName.Text + " is created.");  
   }  
  
   ```  
  
## <a name="see-also"></a><span data-ttu-id="7573b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7573b-126">See Also</span></span>  
 [<span data-ttu-id="7573b-127">使用 WCF LOB 配接器 SDK 所建立的配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="7573b-127">Troubleshoot adapter created using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)