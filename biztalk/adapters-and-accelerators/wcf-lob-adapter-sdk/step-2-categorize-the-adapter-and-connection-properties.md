---
title: 步驟 2： 分類的介面卡和連接屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45b3dc64-2078-4008-878b-501f727f4a11
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e9d49323695b1070a8065cf7a5e548e61fc5db9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226822"
---
# <a name="step-2-categorize-the-adapter-and-connection-properties"></a><span data-ttu-id="66e5f-102">步驟 2： 分類的介面卡和連接屬性</span><span class="sxs-lookup"><span data-stu-id="66e5f-102">Step 2: Categorize the Adapter and Connection Properties</span></span>
<span data-ttu-id="66e5f-103">![步驟 2 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")</span><span class="sxs-lookup"><span data-stu-id="66e5f-103">![Step 2 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")</span></span>  
  
 <span data-ttu-id="66e5f-104">**若要完成的時間：** 30 分鐘</span><span class="sxs-lookup"><span data-stu-id="66e5f-104">**Time to complete:** 30 minutes</span></span>  
  
 <span data-ttu-id="66e5f-105">在此步驟中，您會更新**EchoAdapterBindingElement**和**EchoAdapterBindingElementExtensionElement**類別來指定您的配接器和連接屬性的類別。</span><span class="sxs-lookup"><span data-stu-id="66e5f-105">In this step, you update the **EchoAdapterBindingElement** and **EchoAdapterBindingElementExtensionElement** classes to assign a category to your adapter and connection properties.</span></span> <span data-ttu-id="66e5f-106">如此一來，屬性會以邏輯方式分組中依分類[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具。</span><span class="sxs-lookup"><span data-stu-id="66e5f-106">By doing so, properties are logically grouped by category in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] tools.</span></span> <span data-ttu-id="66e5f-107">比方說，如果您想要**應用程式**， **EnableAuthentication**，和**Hostname**屬性下方出現**連接**類別如下所示，您需要將連接類別指派給每個應用程式、 EnableAuthentication 及主機名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="66e5f-107">For example, if you want the **Application**, **EnableAuthentication**, and **Hostname** properties to appear under the **Connection** category as shown below, you need to assign the Connection category to each of the Application, EnableAuthentication, and Hostname properties.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/c7c0c013-6651-4c32-9f8b-b546a68a0267.gif "c7c0c013-6651-4c32-9f8b-b546a68a0267")  
  
 <span data-ttu-id="66e5f-108">同樣地，如果您想**InboundFileFilter**和**InboundFleSystemWatcherFolder**屬性下方出現**輸入**類別如下所示，您需要為每個指派輸入類別目錄。</span><span class="sxs-lookup"><span data-stu-id="66e5f-108">Similarly, if you want the **InboundFileFilter** and **InboundFleSystemWatcherFolder** properties to appear under the **Inbound** category as shown below, you need to assign the Inbound category to each.</span></span> <span data-ttu-id="66e5f-109">如果您想**計數**和**EnableConnectionPooling**下方出現**其他**分類中，您需要為每個指派其他類別目錄。</span><span class="sxs-lookup"><span data-stu-id="66e5f-109">If you want **Count** and **EnableConnectionPooling** to appear under the **Misc** category, you need to assign the Misc category to each.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/2acb7677-8b50-4e45-96a3-42d0e2011f19.gif "2acb7677-8b50-4e45-96a3-42d0e2011f19")  
  
 <span data-ttu-id="66e5f-110">請記住，您可以指定具有您所選擇的任何類別目錄名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="66e5f-110">Keep in mind that you can assign a property with any category name you choose.</span></span> <span data-ttu-id="66e5f-111">在此範例中，因為 EnableConnnectionPooling 屬性不屬於其他類別，我們將分類它做為其他 （其他）。</span><span class="sxs-lookup"><span data-stu-id="66e5f-111">In this example, since the EnableConnnectionPooling property does not belong to any other categories, we categorize it as Misc (Miscellaneous).</span></span> <span data-ttu-id="66e5f-112">對於 InboundFileFilter 屬性中，因為它用在此範例中，輸入處理期間則會更適當地將輸入指派給屬性，而不是其他。</span><span class="sxs-lookup"><span data-stu-id="66e5f-112">As to the InboundFileFilter property, since it is used during the inbound handling within the example, it is more appropriate to assign Inbound to the property, rather than Miscellaneous.</span></span> <span data-ttu-id="66e5f-113">以下是回應配接器為完整的自訂屬性分類。</span><span class="sxs-lookup"><span data-stu-id="66e5f-113">Here is the complete custom property categorization for the echo adapter.</span></span>  
  
|<span data-ttu-id="66e5f-114">**屬性**</span><span class="sxs-lookup"><span data-stu-id="66e5f-114">**Property**</span></span>|<span data-ttu-id="66e5f-115">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="66e5f-115">**Category**</span></span>|  
|------------------|------------------|  
|<span data-ttu-id="66e5f-116">InboundFileFilter</span><span class="sxs-lookup"><span data-stu-id="66e5f-116">InboundFileFilter</span></span>|<span data-ttu-id="66e5f-117">輸入</span><span class="sxs-lookup"><span data-stu-id="66e5f-117">Inbound</span></span>|  
|<span data-ttu-id="66e5f-118">InboundFileSystemWatcherFolder</span><span class="sxs-lookup"><span data-stu-id="66e5f-118">InboundFileSystemWatcherFolder</span></span>|<span data-ttu-id="66e5f-119">輸入</span><span class="sxs-lookup"><span data-stu-id="66e5f-119">Inbound</span></span>|  
|<span data-ttu-id="66e5f-120">Count</span><span class="sxs-lookup"><span data-stu-id="66e5f-120">Count</span></span>|<span data-ttu-id="66e5f-121">其他</span><span class="sxs-lookup"><span data-stu-id="66e5f-121">Misc</span></span>|  
|<span data-ttu-id="66e5f-122">EnableConnectionPooling</span><span class="sxs-lookup"><span data-stu-id="66e5f-122">EnableConnectionPooling</span></span>|<span data-ttu-id="66e5f-123">其他</span><span class="sxs-lookup"><span data-stu-id="66e5f-123">Misc</span></span>|  
|<span data-ttu-id="66e5f-124">應用程式</span><span class="sxs-lookup"><span data-stu-id="66e5f-124">Application</span></span>|<span data-ttu-id="66e5f-125">連接</span><span class="sxs-lookup"><span data-stu-id="66e5f-125">Connection</span></span>|  
|<span data-ttu-id="66e5f-126">EnableAuthentication</span><span class="sxs-lookup"><span data-stu-id="66e5f-126">EnableAuthentication</span></span>|<span data-ttu-id="66e5f-127">連接</span><span class="sxs-lookup"><span data-stu-id="66e5f-127">Connection</span></span>|  
|<span data-ttu-id="66e5f-128">主機名稱</span><span class="sxs-lookup"><span data-stu-id="66e5f-128">Hostname</span></span>|<span data-ttu-id="66e5f-129">連接</span><span class="sxs-lookup"><span data-stu-id="66e5f-129">Connection</span></span>|  
|<span data-ttu-id="66e5f-130">EchoInUpperCase</span><span class="sxs-lookup"><span data-stu-id="66e5f-130">EchoInUpperCase</span></span>|<span data-ttu-id="66e5f-131">格式</span><span class="sxs-lookup"><span data-stu-id="66e5f-131">Format</span></span>|  
  
 <span data-ttu-id="66e5f-132">除了這些變更，您也修改的 Dispose 方法**EchoAdapterHandlerBase**。</span><span class="sxs-lookup"><span data-stu-id="66e5f-132">In addition to those changes, you also modify the Dispose method of **EchoAdapterHandlerBase**.</span></span>  
  
 <span data-ttu-id="66e5f-133">如回應配接器所公開的配接器屬性，請參閱配接器的 properties 區段[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="66e5f-133">For the adapter properties exposed by the echo adapter, see the adapter properties section of the [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="66e5f-134">必要條件</span><span class="sxs-lookup"><span data-stu-id="66e5f-134">Prerequisites</span></span>  
 <span data-ttu-id="66e5f-135">在開始此步驟之前，必須先完成[步驟 1： 使用 WCF LOB 配接器開發精靈來建立回應配接器專案](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-wcf-lob-adapter-development-wizard-to-create-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="66e5f-135">Before you begin this step, you must complete [Step 1: Use the WCF LOB Adapter Development Wizard to Create the Echo Adapter Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-wcf-lob-adapter-development-wizard-to-create-the-echo-adapter.md).</span></span> <span data-ttu-id="66e5f-136">您也應該熟悉`System.ServiceModel.Configuration.BindingElementExtensionElement`和`System.ServiceModel.Configuration.StandardBindingElement`類別。</span><span class="sxs-lookup"><span data-stu-id="66e5f-136">You should also be familiar with the `System.ServiceModel.Configuration.BindingElementExtensionElement` and `System.ServiceModel.Configuration.StandardBindingElement` classes.</span></span>  
  
## <a name="update-the-echoadapterhandlerbase-dispose-method"></a><span data-ttu-id="66e5f-137">更新 EchoAdapterHandlerBase Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="66e5f-137">Update the EchoAdapterHandlerBase Dispose method</span></span>  
  
1.  <span data-ttu-id="66e5f-138">在**方案總管 中**，連按兩下**EchoAdapterHandlerBase.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="66e5f-138">In **Solution Explorer**, double-click the **EchoAdapterHandlerBase.cs** file.</span></span>  
  
2.  <span data-ttu-id="66e5f-139">移除下列陳述式從**處置**方法：</span><span class="sxs-lookup"><span data-stu-id="66e5f-139">Remove the following statement from the **Dispose** method:</span></span>  
  
    ```csharp  
    throw new NotImplementedException("The method or operation is not implemented.");  
    ```  
  
     <span data-ttu-id="66e5f-140">修改過的方法看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="66e5f-140">The revised method should look similar to the following:</span></span>  
  
    ```csharp  
    protected virtual void Dispose(bool disposing)  
    {  
       //  
       //TODO: Implement Dispose. Override this method in respective Handler classes  
       //  
    }  
    ```  
  
## <a name="update-the-adapter-properties-class"></a><span data-ttu-id="66e5f-141">更新配接器屬性類別</span><span class="sxs-lookup"><span data-stu-id="66e5f-141">Update the Adapter properties class</span></span>  
  
1.  <span data-ttu-id="66e5f-142">在**方案總管 中**，連按兩下**EchoAdapterBindingElement.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="66e5f-142">In **Solution Explorer**, double-click the **EchoAdapterBindingElement.cs** file.</span></span>  
  
2.  <span data-ttu-id="66e5f-143">在 Visual Studio 編輯器中，展開 **自訂產生屬性**區域。</span><span class="sxs-lookup"><span data-stu-id="66e5f-143">In the Visual Studio editor, expand the **Custom Generated Properties** region.</span></span>  
  
3.  <span data-ttu-id="66e5f-144">若要指派**其他**類別**計數**屬性，加入下列單一陳述式的開頭**計數**實作。</span><span class="sxs-lookup"><span data-stu-id="66e5f-144">To assign the **Misc** category to the **Count** property, add the following single statement to the beginning of the **Count** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    ```  
  
     <span data-ttu-id="66e5f-145">**計數**實作現在應符合下列：</span><span class="sxs-lookup"><span data-stu-id="66e5f-145">The **Count** implementation should now match the following:</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("count", DefaultValue = 5)]  
    public int Count  
    {  
        get  
        {  
            return ((int)(base["Count"]));  
        }  
        set  
        {  
            base["Count"] = value;  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="66e5f-146">若要指派**其他**類別**EnableConnectionPooling**屬性，加入下列單一陳述式的開頭**EnableConnectionPooling**實作。</span><span class="sxs-lookup"><span data-stu-id="66e5f-146">To assign the **Misc** category to the **EnableConnectionPooling** property, add the following single statement to the beginning of the **EnableConnectionPooling** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    ```  
  
5.  <span data-ttu-id="66e5f-147">若要指派**輸入**類別**InboundFileFilter**屬性，加入下列單一陳述式的開頭**InboundFileFilter**實作。</span><span class="sxs-lookup"><span data-stu-id="66e5f-147">To assign the **Inbound** category to the **InboundFileFilter** property, add the following single statement to the beginning of the **InboundFileFilter** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Inbound")]  
    ```  
  
6.  <span data-ttu-id="66e5f-148">若要指派**輸入**categoryto **inboundFleSystemWatcherFolder**屬性，加入下列單一陳述式的開頭**inboundFleSystemWatcherFolder**實作。</span><span class="sxs-lookup"><span data-stu-id="66e5f-148">To assign the **Inbound** categoryto **inboundFleSystemWatcherFolder** property, add the following single statement to the beginning of the **inboundFleSystemWatcherFolder** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Inbound")]  
    ```  
  
7.  <span data-ttu-id="66e5f-149">請確認程式碼中的核取**自訂產生屬性**區符合下列：</span><span class="sxs-lookup"><span data-stu-id="66e5f-149">Check to ensure that the code in the **Custom Generated Properties** region matches the following:</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("count", DefaultValue = 5)]  
    public int Count  
    {  
        get  
        {  
            return ((int)(base["Count"]));  
        }  
        set  
        {  
            base["Count"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("enableConnectionPooling", DefaultValue = true)]  
    public bool EnableConnectionPooling  
    {  
        get  
        {  
            return ((bool)(base["EnableConnectionPooling"]));  
        }  
        set  
        {  
            base["EnableConnectionPooling"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("Inbound")]  
    [System.Configuration.ConfigurationProperty("inboundFileFilter", DefaultValue = "*.txt")]  
    public string InboundFileFilter  
    {  
        get  
        {  
            return ((string)(base["InboundFileFilter"]));  
        }  
        set  
        {  
            base["InboundFileFilter"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("Inbound")]  
    [System.Configuration.ConfigurationProperty("inboundFileSystemWatcherFolder", DefaultValue = "{InboundFileSystemWatcherFolder}")]  
    public string InboundFileSystemWatcherFolder  
    {  
        get  
        {  
            return ((string)(base["InboundFileSystemWatcherFolder"]));  
        }  
        set  
        {  
            base["InboundFileSystemWatcherFolder"] = value;  
        }  
    }  
  
    #endregion Custom Generated Properties  
    ```  
  
## <a name="update-the-connection-properties"></a><span data-ttu-id="66e5f-150">更新連接屬性</span><span class="sxs-lookup"><span data-stu-id="66e5f-150">Update the Connection Properties</span></span>  
  
1.  <span data-ttu-id="66e5f-151">在**方案總管 中**，連按兩下**EchoAdapterConnectionUri.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="66e5f-151">In **Solution Explorer**, double-click the **EchoAdapterConnectionUri.cs** file.</span></span>  
  
2.  <span data-ttu-id="66e5f-152">在 Visual Studio 編輯器中，展開 **自訂產生屬性**區域。</span><span class="sxs-lookup"><span data-stu-id="66e5f-152">In the Visual Studio editor, expand the **Custom Generated Properties** region.</span></span>  
  
3.  <span data-ttu-id="66e5f-153">若要指派**格式**類別**EchoInUpperCase**屬性，加入下列單一陳述式的開頭**EchoInUpperCase**實作。</span><span class="sxs-lookup"><span data-stu-id="66e5f-153">To assign the **Format** category to the **EchoInUpperCase** property, add the following single statement to the beginning of the **EchoInUpperCase** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Format")]  
    ```  
  
4.  <span data-ttu-id="66e5f-154">若要指派**連接**類別**Hostname**屬性，開頭新增下列單一陳述式**主機名稱**實作。</span><span class="sxs-lookup"><span data-stu-id="66e5f-154">To assign the **Connection** category to the **Hostname** property, add the following single statement to the beginning of the **Hostname** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
5.  <span data-ttu-id="66e5f-155">若要指派**連接**類別**應用程式**屬性，新增下列單一陳述式的開頭**應用程式**實作。</span><span class="sxs-lookup"><span data-stu-id="66e5f-155">To assign the **Connection** category to the **Application** property, add the following single statement to the beginning of the **Application** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
6.  <span data-ttu-id="66e5f-156">若要指派**連接**categoryto **EnableAuthentication**屬性，加入下列單一陳述式的開頭**EnableAuthentication**實作。</span><span class="sxs-lookup"><span data-stu-id="66e5f-156">To assign the **Connection** categoryto **EnableAuthentication** property, add the following single statement to the beginning of the **EnableAuthentication** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
7.  <span data-ttu-id="66e5f-157">請確認程式碼中的核取**自訂產生屬性**區符合下列：</span><span class="sxs-lookup"><span data-stu-id="66e5f-157">Check to ensure that the code in the **Custom Generated Properties** region matches the following:</span></span>  
  
    ```csharp  
    #region Custom Generated Properties  
            [System.ComponentModel.Category("Format")]  
            public bool EchoInUpperCase  
            {  
                get  
                {  
                    return this.echoInUpperCase;  
                }  
                set  
                {  
                    this.echoInUpperCase = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public string Hostname  
            {  
                get  
                {  
                    return this.hostname;  
                }  
                set  
                {  
                    this.hostname = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public string Application  
            {  
                get  
                {  
                    return this.application;  
                }  
                set  
                {  
                    this.application = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public bool EnableAuthentication  
            {  
                get  
                {  
                    return this.enableAuthentication;  
                }  
                set  
                {  
                    this.enableAuthentication = value;  
                }  
            }  
            #endregion Custom Generated Properties  
    ```  
  
8.  <span data-ttu-id="66e5f-158">在 Visual Studio 中，從**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="66e5f-158">In Visual Studio, from the **File** menu, click **Save All**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66e5f-159">您應該已經儲存您的工作結果。</span><span class="sxs-lookup"><span data-stu-id="66e5f-159">You saved your work.</span></span> <span data-ttu-id="66e5f-160">您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 3： 實作 Echo 介面卡的連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="66e5f-160">You can safely close Visual Studio at this time or go to the next step, [Step 3: Implement the Connection for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="66e5f-161">我剛剛做什麼？</span><span class="sxs-lookup"><span data-stu-id="66e5f-161">What Did I Just Do?</span></span>  
 <span data-ttu-id="66e5f-162">剛更新的類別，以回應配接器所公開的每個配接器和連接屬性中指定的類別。</span><span class="sxs-lookup"><span data-stu-id="66e5f-162">You just updated classes to assign a category to each adapter and connection property exposed by the echo adapter.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="66e5f-163">後續步驟</span><span class="sxs-lookup"><span data-stu-id="66e5f-163">Next Steps</span></span>  
 <span data-ttu-id="66e5f-164">您可以實作連接、 中繼資料瀏覽、 搜尋和解析功能，以及輸出的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="66e5f-164">You implement connection, metadata browsing, searching, and resolving capabilities, and the outbound message exchange.</span></span> <span data-ttu-id="66e5f-165">最後，您會建置並部署回應配接器。</span><span class="sxs-lookup"><span data-stu-id="66e5f-165">Lastly, you build and deploy the echo adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e5f-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66e5f-166">See Also</span></span>  
 <span data-ttu-id="66e5f-167">[步驟 3： 實作 Echo 介面卡的連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="66e5f-167">[Step 3: Implement the Connection for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="66e5f-168">教學課程 1： 在開發回應配接器</span><span class="sxs-lookup"><span data-stu-id="66e5f-168">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)