---
title: "如何啟用 WCF 擴充性點，WCF 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, WCF adapters
- WCF adapters, extensibility ports
ms.assetid: 0c2af105-5272-4a6a-95d2-066312ab788e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e481521ba651fe8c1e66ea4f730d05375451f111
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters"></a><span data-ttu-id="8abf4-102">如何使用 WCF 配接器啟用 WCF 擴充性點</span><span class="sxs-lookup"><span data-stu-id="8abf4-102">How to Enable the WCF Extensibility Points with the WCF Adapters</span></span>
<span data-ttu-id="8abf4-103">本主題描述如何啟用三個 WCF 擴充性點： 行為延伸模組、 繫結元素延伸模組，以及繫結延伸模組，使用 Wcf-custom 和 Wcf-customisolated 配接器。</span><span class="sxs-lookup"><span data-stu-id="8abf4-103">This topic describes how to enable three WCF extensibility points—behavior extension, binding element extension, and binding extension—with the WCF-Custom and WCF-CustomIsolated adapters.</span></span> <span data-ttu-id="8abf4-104">為了執行這項操作，您會先將實作 WCF 擴充性點的組件安裝在全域組件快取 (GAC) 中，接著修改電腦上的 machine.config 檔案，然後再使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台設定 WCF-Custom 或 WCF-CustomIsolated 配接器。</span><span class="sxs-lookup"><span data-stu-id="8abf4-104">To do so, you first install the assemblies implementing the WCF extensibility points in the global assembly cache (GAC), then modify the machine.config file on your computers, and then configure the WCF-Custom or the WCF-CustomIsolated adapter by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="8abf4-105">WCF 擴充性點的詳細資訊，請參閱 < 延伸 WCF >，網址[http://go.microsoft.com/fwlink/?LinkId=86380](http://go.microsoft.com/fwlink/?LinkId=86380)。</span><span class="sxs-lookup"><span data-stu-id="8abf4-105">For more information about the WCF extensibility points, see "Extending WCF" at [http://go.microsoft.com/fwlink/?LinkId=86380](http://go.microsoft.com/fwlink/?LinkId=86380).</span></span>  
  
 <span data-ttu-id="8abf4-106">如何啟用 WCF 擴充性點的詳細資訊，請參閱 < SDK 範例:: 使用自訂繫結延伸模組使用 Wcf-custom 配接器 >，網址[http://go.microsoft.com/fwlink/?LinkId=65185](http://go.microsoft.com/fwlink/?LinkId=65185)。</span><span class="sxs-lookup"><span data-stu-id="8abf4-106">For more information about how to enable the WCF extensibility points, see "SDK Sample: Using Custom Binding Extensions with the WCF-Custom Adapters" at [http://go.microsoft.com/fwlink/?LinkId=65185](http://go.microsoft.com/fwlink/?LinkId=65185).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8abf4-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="8abf4-107">Prerequisites</span></span>  
 <span data-ttu-id="8abf4-108">若要執行這個主題中的程序，您必須使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="8abf4-108">To perform the procedures in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span> <span data-ttu-id="8abf4-109">如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8abf4-109">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-install-assemblies-implementing-a-wcf-extensibility-point-in-the-gac"></a><span data-ttu-id="8abf4-110">若要將實作 WCF 擴充性點的組件安裝在 GAC 中</span><span class="sxs-lookup"><span data-stu-id="8abf4-110">To install assemblies implementing a WCF extensibility point in the GAC</span></span>  
  
1.  <span data-ttu-id="8abf4-111">將實作 WCF 擴充性點的組件複製到本機電腦的資料夾。</span><span class="sxs-lookup"><span data-stu-id="8abf4-111">Copy the assemblies implementing the WCF extensibility point to a folder on your local computer.</span></span>  
  
2.  <span data-ttu-id="8abf4-112">將 WCF 擴充性點使用的組件 (如果有的話) 複製到本機電腦的資料夾。</span><span class="sxs-lookup"><span data-stu-id="8abf4-112">Copy the assemblies that the WCF extensibility point uses, if any, to a folder on your local computer.</span></span>  
  
3.  <span data-ttu-id="8abf4-113">啟動**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-113">Start the **Visual Studio Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="8abf4-114">輸入以下命令：</span><span class="sxs-lookup"><span data-stu-id="8abf4-114">Type the following command:</span></span>  
  
     <span data-ttu-id="8abf4-115">**gacutil.exe /if"\<**  *組件.dll 檔案路徑* **> 」**</span><span class="sxs-lookup"><span data-stu-id="8abf4-115">**gacutil.exe /if "\<** *path to the assembly .dll file* **>"**</span></span>  
  
5.  <span data-ttu-id="8abf4-116">這會將組件安裝至 GAC，覆寫任何同名的現有組件。</span><span class="sxs-lookup"><span data-stu-id="8abf4-116">This installs the assembly to the GAC, overwriting any existing assembly that has the same assembly name.</span></span>  
  
6.  <span data-ttu-id="8abf4-117">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令提示字元下，針對您在本程序步驟 1 和 2 中複製的所有組件重複步驟 4 和 5。</span><span class="sxs-lookup"><span data-stu-id="8abf4-117">At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, repeat steps 4 and 5 against all the assemblies you copied in steps 1 and 2 of this procedure.</span></span>  
  
7.  <span data-ttu-id="8abf4-118">如果您有多個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦和管理電腦，重複步驟 1 到 6，此程序的所有電腦上。</span><span class="sxs-lookup"><span data-stu-id="8abf4-118">If you have multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers and administration computers, repeat steps 1 through 6 of this procedure on all the computers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-119">若要啟用 WCF 配接器的 WCF 擴充性點，執行配接器的 BizTalk 主控件執行個體必須能夠在執行階段載入實作 WCF 擴充性點的組件。</span><span class="sxs-lookup"><span data-stu-id="8abf4-119">To enable WCF extensibility points for the WCF adapters, the BizTalk Host instance running the adapter must be able to load at run time the assemblies where the WCF extensibility points are implemented.</span></span>  
  
### <a name="to-configure-the-machineconfig-file-for-a-wcf-binding-extension"></a><span data-ttu-id="8abf4-120">若要設定 WCF 繫結延伸模組的 machine.config 檔案</span><span class="sxs-lookup"><span data-stu-id="8abf4-120">To configure the machine.config file for a WCF binding extension</span></span>  
  
1.  <span data-ttu-id="8abf4-121">在命令提示字元中，移至 %frameworkdir%\v4。X.XXXXX\CONFIG 資料夾，然後開啟**machine.config**使用 [記事本] 檔案。</span><span class="sxs-lookup"><span data-stu-id="8abf4-121">At a command prompt, go to the %FrameworkDir%\v4.X.XXXXX\CONFIG folder, and then open the **machine.config** file by using Notepad.</span></span>  
  
2.  <span data-ttu-id="8abf4-122">在記事本中，如果 machine.config 檔案沒有 **\<system.serverModel >\\< 延伸\>**項目，加入這些項目內 **\<設定 >**元素的 machine.config 檔案，然後再加入 **\<bindingExtensions >** WCF 繫結延伸模組內的項目 **\<system.serverModel >\\< 延伸\>**項目。</span><span class="sxs-lookup"><span data-stu-id="8abf4-122">In Notepad, if the machine.config file does not have the **\<system.serverModel>\\<extensions\>** elements, add those elements inside the **\<configuration>** element of the machine.config file, and then add the **\<bindingExtensions>** element for a WCF binding extension inside the **\<system.serverModel>\\<extensions\>** elements.</span></span> <span data-ttu-id="8abf4-123">例如，若要啟用自訂繫結延伸模組 netHttpBinding，請加入內的下列程式碼**\<組態 >** machine.config 檔案的項目：</span><span class="sxs-lookup"><span data-stu-id="8abf4-123">For example, to enable a custom binding extension, netHttpBinding, add the following code inside the **\<configuration>** element of the machine.config file:</span></span>  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <bindingExtensions>  
          <add name="netHttpBinding" type="Microsoft.Samples.Channels.NetHttpBindingCollectionElement, NetHttpBinding, Version=3.0.0.0, Culture=neutral, PublicKeyToken=5b637b51c4aaa2a8" />  
        </bindingExtensions>        
      </extensions>  
    </system.serviceModel>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-124">您可以找到要使用命令，註冊的組件的資訊**gacutil /lr** *< assembly_name>*。</span><span class="sxs-lookup"><span data-stu-id="8abf4-124">You can find the information for the assemblies to register by using the command, **gacutil /lr** *<assembly_name>*.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-125">如需有關 **<bindingExtensions>** 項目，請參閱 「<bindingExtensions>」 在[http://go.microsoft.com/fwlink/?LinkID=86180](http://go.microsoft.com/fwlink/?LinkID=86180)。</span><span class="sxs-lookup"><span data-stu-id="8abf4-125">For more information about the **<bindingExtensions>** element, see "<bindingExtensions>" at [http://go.microsoft.com/fwlink/?LinkID=86180](http://go.microsoft.com/fwlink/?LinkID=86180).</span></span>  
  
3.  <span data-ttu-id="8abf4-126">在「記事本」中，儲存 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="8abf4-126">In Notepad, save the machine.config file.</span></span>  
  
4.  <span data-ttu-id="8abf4-127">如果您有多部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦和管理電腦，請在所有電腦上重複本程序的步驟 1 到 3。</span><span class="sxs-lookup"><span data-stu-id="8abf4-127">If you have multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers and administration computers, repeat steps 1 through 3 of this procedure on all the computers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-128">您必須在所有電腦上重複這些步驟，WCF 基礎結構才能處理 BizTalk 主控件執行個體和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台的 WCF 擴充性點。</span><span class="sxs-lookup"><span data-stu-id="8abf4-128">You have to repeat these steps on all the computers for the WCF infrastructure to process the WCF extensibility point for the BizTalk Host instance and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
### <a name="to-configure-a-wcf-binding-extension-by-using-the-biztalk-administration-console"></a><span data-ttu-id="8abf4-129">若要使用 BizTalk 管理主控台設定 WCF 繫結延伸模組</span><span class="sxs-lookup"><span data-stu-id="8abf4-129">To configure a WCF binding extension by using the BizTalk Administration console</span></span>  
  
1.  <span data-ttu-id="8abf4-130">按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-130">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-131">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台已經開啟，請重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8abf4-131">If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console is already opened, restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="8abf4-132">如果您使用 WCF-Custom 配接器，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，依序展開 [平台設定] 和 [主控件執行個體]，然後再重新啟動執行該配接器的 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8abf4-132">If you use the WCF-Custom adapter, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand Platform Settings, expand Host Instances, and then restart the BizTalk Host instance running the adapter.</span></span>  
  
3.  <span data-ttu-id="8abf4-133">如果您使用 WCF-CustomIsolated 配接器，請在 IIS 管理主控台中，重新啟動與 WCF 接收位置關聯的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="8abf4-133">If you use the WCF-CustomIsolated adapter, in the IIS Management console, restart the application pool associated with the WCF receive location.</span></span>  
  
4.  <span data-ttu-id="8abf4-134">如果您想要設定接收位置中使用 WCF 擴充性點，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk 群組**，依序展開 *\<BizTalk 應用程式 >*依序展開**接收位置**，然後在右窗格中按兩下*\<接收位置>*。</span><span class="sxs-lookup"><span data-stu-id="8abf4-134">If you want to configure a receive location to use a WCF extensibility point, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand *\<BizTalk application>*, expand **Receive Locations**, and then in the right pane, double-click *\<Receive location>*.</span></span>  
  
    -   <span data-ttu-id="8abf4-135">在**接收位置屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**或**Wcf-customisolated**根據您想要使用，然後按一下 WCF 配接器**設定**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-135">In the **Receive Location Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom** or **WCF-CustomIsolated** depending on the WCF adapter that you want to use, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="8abf4-136">如果您想要設定傳送埠中使用 WCF 擴充性點，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk 群組**，依序展開 *\<BizTalk 應用程式 >*，依序展開**傳送埠**，然後在右窗格中按兩下*\<傳送連接埠>*。</span><span class="sxs-lookup"><span data-stu-id="8abf4-136">If you want to configure a send port to use a WCF extensibility point, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand *\<BizTalk application>*, expand **Send Ports**, and then in the right pane, double-click *\<Send port>*.</span></span>  
  
    -   <span data-ttu-id="8abf4-137">在**傳送埠屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-137">In the **Send Port Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="8abf4-138">在 傳輸屬性對話方塊、 上**繫結**索引標籤上選取繫結延伸模組，然後設定其餘的傳輸設定。</span><span class="sxs-lookup"><span data-stu-id="8abf4-138">In the transport properties dialog box, on the **Binding** tab, select the binding extension, and then configure the rest of the settings for the transport.</span></span>  
  
7.  <span data-ttu-id="8abf4-139">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，按一下關閉所有開啟的對話方塊**確定**按鈕，並確定沒有出現任何錯誤訊息和錯誤事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8abf4-139">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, close all open dialog boxes by clicking the **OK** buttons, and then make sure that no error messages and erroneous event logs appear.</span></span>  
  
### <a name="to-configure-the-machineconfig-file-for-a-wcf-binding-element-extension"></a><span data-ttu-id="8abf4-140">若要設定 WCF 繫結元素延伸模組的 machine.config 檔案</span><span class="sxs-lookup"><span data-stu-id="8abf4-140">To configure the machine.config file for a WCF binding element extension</span></span>  
  
1.  <span data-ttu-id="8abf4-141">在命令提示字元中，移至 %frameworkdir%\v4。X.XXXXX\CONFIG 資料夾，然後開啟**machine.config**使用 [記事本] 檔案。</span><span class="sxs-lookup"><span data-stu-id="8abf4-141">At a command prompt, go to the %FrameworkDir%\v4.X.XXXXX\CONFIG folder, and then open the **machine.config** file by using Notepad.</span></span>  
  
2.  <span data-ttu-id="8abf4-142">在記事本中，如果 machine.config 檔案沒有 **\<system.serverModel >\\< 延伸\>**項目，加入這些項目內 **\<設定 >**元素的 machine.config 檔案，然後再加入 **\<bindingElementExtensions >** WCF 繫結元素延伸模組內的項目 **\<system.serverModel >\\< 延伸\>**項目。</span><span class="sxs-lookup"><span data-stu-id="8abf4-142">In Notepad, if the machine.config file does not have the **\<system.serverModel>\\<extensions\>** elements, add those elements inside the **\<configuration>** element of the machine.config file, and then add the **\<bindingElementExtensions>** element for a WCF binding element extension inside the **\<system.serverModel>\\<extensions\>** elements.</span></span> <span data-ttu-id="8abf4-143">比方說，若要啟用自訂繫結元素延伸模組，請將下列程式碼內**\<組態 >** machine.config 檔案的項目：</span><span class="sxs-lookup"><span data-stu-id="8abf4-143">For example, to enable a custom binding element extension, droppingInterceptor, add the following code inside the **\<configuration>** element of the machine.config file:</span></span>  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <bindingElementExtensions>  
          <add name="droppingInterceptor" type="Microsoft.ServiceModel.Samples.DroppingServerElement, MessageInterceptor, Version=0.0.0.0, Culture=neutral, PublicKeyToken=098514eef14aa34a"/>  
        </bindingElementExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-144">您可以找到要使用命令，註冊的組件的資訊**gacutil /lr** *< assembly_name>*。</span><span class="sxs-lookup"><span data-stu-id="8abf4-144">You can find the information for the assemblies to register by using the command, **gacutil /lr** *<assembly_name>*.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-145">如需有關 **<bindingElementExtensions>** 項目，請參閱 「<bindingElementExtensions>」 在[http://go.microsoft.com/fwlink/?LinkId=86381](http://go.microsoft.com/fwlink/?LinkId=86381)。</span><span class="sxs-lookup"><span data-stu-id="8abf4-145">For more information about the **<bindingElementExtensions>** element, see "<bindingElementExtensions>" at [http://go.microsoft.com/fwlink/?LinkId=86381](http://go.microsoft.com/fwlink/?LinkId=86381).</span></span>  
  
3.  <span data-ttu-id="8abf4-146">在「記事本」中，儲存 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="8abf4-146">In Notepad, save the machine.config file.</span></span>  
  
4.  <span data-ttu-id="8abf4-147">如果您有多部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦和管理電腦，請在所有電腦上重複本程序的步驟 1 到 3。</span><span class="sxs-lookup"><span data-stu-id="8abf4-147">If you have multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers and administration computers, repeat steps 1 through 3 of this procedure on all the computers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-148">您必須在所有電腦上重複這些步驟，WCF 基礎結構才能處理 BizTalk 主控件執行個體和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台的 WCF 擴充性點。</span><span class="sxs-lookup"><span data-stu-id="8abf4-148">You have to repeat these steps on all the computers for the WCF infrastructure to process the WCF extensibility point for the BizTalk Host instance and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
### <a name="to-configure-a-wcf-binding-element-extension-by-using-the-biztalk-administration-console"></a><span data-ttu-id="8abf4-149">若要使用 BizTalk 管理主控台設定 WCF 繫結元素延伸模組</span><span class="sxs-lookup"><span data-stu-id="8abf4-149">To configure a WCF binding element extension by using the BizTalk Administration console</span></span>  
  
1.  <span data-ttu-id="8abf4-150">按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-150">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-151">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台已經開啟，請重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8abf4-151">If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console is already opened, restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="8abf4-152">如果您使用 WCF-Custom 配接器，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，依序展開 [平台設定] 和 [主控件執行個體]，然後再重新啟動執行該配接器的 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8abf4-152">If you use the WCF-Custom adapter, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand Platform Settings, expand Host Instances, and then restart the BizTalk Host instance running the adapter.</span></span>  
  
3.  <span data-ttu-id="8abf4-153">如果您使用 WCF-CustomIsolated 配接器，請在 IIS 管理主控台中，重新啟動與 WCF 接收位置關聯的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="8abf4-153">If you use the WCF-CustomIsolated adapter, in the IIS Management console, restart the application pool associated with the WCF receive location.</span></span>  
  
4.  <span data-ttu-id="8abf4-154">如果您想要設定接收位置中使用 WCF 擴充性點，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk 群組**，依序展開 *\<BizTalk 應用程式 >*依序展開**接收位置**，然後在右窗格中按兩下*\<接收位置>*。</span><span class="sxs-lookup"><span data-stu-id="8abf4-154">If you want to configure a receive location to use a WCF extensibility point, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand *\<BizTalk application>*, expand **Receive Locations**, and then in the right pane, double-click *\<Receive location>*.</span></span>  
  
    -   <span data-ttu-id="8abf4-155">在**接收位置屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**或**Wcf-customisolated**根據您想要使用，然後按一下 WCF 配接器**設定**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-155">In the **Receive Location Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom** or **WCF-CustomIsolated** depending on the WCF adapter that you want to use, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="8abf4-156">如果您想要設定傳送埠中使用 WCF 擴充性點，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk 群組**，依序展開 *\<BizTalk 應用程式 >*，依序展開**傳送埠**，然後在右窗格中按兩下*\<傳送連接埠>*。</span><span class="sxs-lookup"><span data-stu-id="8abf4-156">If you want to configure a send port to use a WCF extensibility point, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand *\<BizTalk application>*, expand **Send Ports**, and then in the right pane, double-click *\<Send port>*.</span></span>  
  
    -   <span data-ttu-id="8abf4-157">在**傳送埠屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-157">In the **Send Port Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="8abf4-158">在 傳輸屬性對話方塊、 上**繫結**索引標籤的**繫結的型別**下拉式清單中，選取**customBinding**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-158">In the transport properties dialog box, on the **Binding** tab, in the **Binding Type** drop-down list, select **customBinding**.</span></span>  
  
7.  <span data-ttu-id="8abf4-159">在 傳輸屬性對話方塊、 上**繫結**索引標籤上，以滑鼠右鍵按一下工作區**繫結**清單，然後再按**將延伸加入**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-159">In the transport properties dialog box, on the **Binding** tab, right-click the client area of the **Binding** list, and then click **Add extension**.</span></span>  
  
8.  <span data-ttu-id="8abf4-160">在**選取繫結元素延伸模組**對話方塊中，選取繫結項目延伸，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-160">In the **Select Binding Element Extension** dialog box, select a binding element extension, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="8abf4-161">在 傳輸屬性對話方塊、 上**繫結**索引標籤上，調整繫結項目中加入的順序**繫結**清單取決於您在加入的繫結項目延伸的類型如下所示的上一個步驟：</span><span class="sxs-lookup"><span data-stu-id="8abf4-161">In the transport properties dialog box, on the **Binding** tab, adjust the order of the binding elements added in the **Binding** list depending on the type of the binding element extension you added in the previous step as follows:</span></span>  
  
    -   <span data-ttu-id="8abf4-162">在**繫結**清單中，繫結項目延伸，以滑鼠右鍵按一下，然後按一下 **移延伸模組**或**下移延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-162">In the **Binding** list, right-click a binding element extension, and then click **Move extension up** or **Move extension down**.</span></span> <span data-ttu-id="8abf4-163">最低的繫結項目延伸中**繫結**對應至通道堆疊的底部元件的清單。</span><span class="sxs-lookup"><span data-stu-id="8abf4-163">The lowest binding element extension in the **Binding** list corresponds to the bottom component of the channel stack.</span></span> <span data-ttu-id="8abf4-164">中最高的繫結項目**繫結**清單對應於通訊堆疊的最上層元件。</span><span class="sxs-lookup"><span data-stu-id="8abf4-164">The highest binding element in the **Binding** list corresponds to the top component of the communication stack.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8abf4-165">自訂繫結的特定繫結項目順序的詳細資訊，請參閱 「 自訂繫結 」，網址[http://go.microsoft.com/fwlink/?LinkId=86383](http://go.microsoft.com/fwlink/?LinkId=86383)。</span><span class="sxs-lookup"><span data-stu-id="8abf4-165">For more information about the specific order of the binding elements for the custom binding, see "Custom Bindings" at [http://go.microsoft.com/fwlink/?LinkId=86383](http://go.microsoft.com/fwlink/?LinkId=86383).</span></span>  
  
10. <span data-ttu-id="8abf4-166">在傳輸屬性對話方塊中，設定其餘的傳輸設定。</span><span class="sxs-lookup"><span data-stu-id="8abf4-166">In the transport properties dialog box, configure the rest of the settings for the transport.</span></span>  
  
11. <span data-ttu-id="8abf4-167">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，按一下關閉所有開啟的對話方塊**確定**按鈕，並確定沒有出現任何錯誤訊息和錯誤事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8abf4-167">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, close all open dialog boxes by clicking the **OK** buttons, and then make sure that no error messages and erroneous event logs appear.</span></span>  
  
### <a name="to-configure-the-machineconfig-file-for-a-wcf-behavior-extension"></a><span data-ttu-id="8abf4-168">若要設定 WCF 行為延伸模組的 machine.config 檔案</span><span class="sxs-lookup"><span data-stu-id="8abf4-168">To configure the machine.config file for a WCF behavior extension</span></span>  
  
1.  <span data-ttu-id="8abf4-169">在命令提示字元中，移至 %frameworkdir%\v4。X.XXXXX\CONFIG 資料夾，然後開啟**machine.config**使用 [記事本] 檔案。</span><span class="sxs-lookup"><span data-stu-id="8abf4-169">At a command prompt, go to the %FrameworkDir%\v4.X.XXXXX\CONFIG folder, and then open the **machine.config** file by using Notepad.</span></span>  
  
2.  <span data-ttu-id="8abf4-170">在記事本中，如果 machine.config 檔案沒有 **\<system.serverModel >\\< 延伸\>**項目，加入這些項目內 **\<設定 >**元素的 machine.config 檔案，然後再加入 **\<behaviorExtensions >** WCF 行為延伸模組內的項目 **\<system.serverModel >\\< 延伸\>**項目。</span><span class="sxs-lookup"><span data-stu-id="8abf4-170">In Notepad, if the machine.config file does not have the **\<system.serverModel>\\<extensions\>** elements, add those elements inside the **\<configuration>** element of the machine.config file, and then add the **\<behaviorExtensions>** element for a WCF behavior extension inside the **\<system.serverModel>\\<extensions\>** elements.</span></span> <span data-ttu-id="8abf4-171">比方說，若要啟用自訂行為延伸模組 schemaValidator，請將下列程式碼內**\<組態 >** machine.config 檔案的項目：</span><span class="sxs-lookup"><span data-stu-id="8abf4-171">For example, To enable a custom behavior extension, schemaValidator, add the following code inside the **\<configuration>** element of the machine.config file:</span></span>  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ad307e213604f592"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-172">您可以找到要使用命令，註冊的組件的資訊**gacutil /lr** *< assembly_name>*。</span><span class="sxs-lookup"><span data-stu-id="8abf4-172">You can find the information for the assemblies to register by using the command, **gacutil /lr** *<assembly_name>*.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-173">如需有關 **<behaviorExtensions>** 項目，請參閱 「<behaviorExtensions>」 在[http://go.microsoft.com/fwlink/?LinkId=86382](http://go.microsoft.com/fwlink/?LinkId=86382)。</span><span class="sxs-lookup"><span data-stu-id="8abf4-173">For more information about the **<behaviorExtensions>** element, see "<behaviorExtensions>" at  [http://go.microsoft.com/fwlink/?LinkId=86382](http://go.microsoft.com/fwlink/?LinkId=86382).</span></span>  
  
3.  <span data-ttu-id="8abf4-174">在「記事本」中，儲存 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="8abf4-174">In Notepad, save the machine.config file.</span></span>  
  
4.  <span data-ttu-id="8abf4-175">如果您有多部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦和管理電腦，請在所有電腦上重複本程序的步驟 1 到 3。</span><span class="sxs-lookup"><span data-stu-id="8abf4-175">If you have multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers and administration computers, repeat steps 1 through 3 of this procedure on all the computers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-176">您必須在所有電腦上重複這些步驟，WCF 基礎結構才能處理 BizTalk 主控件執行個體和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台的 WCF 擴充性點。</span><span class="sxs-lookup"><span data-stu-id="8abf4-176">You have to repeat these steps on all the computers for the WCF infrastructure to process the WCF extensibility point for the BizTalk Host instance and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
### <a name="to-configure-a-wcf-behavior-extension-by-using-the-biztalk-administration-console"></a><span data-ttu-id="8abf4-177">若要使用 BizTalk 管理主控台設定 WCF 行為延伸模組</span><span class="sxs-lookup"><span data-stu-id="8abf4-177">To configure a WCF behavior extension by using the BizTalk Administration console</span></span>  
  
1.  <span data-ttu-id="8abf4-178">按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-178">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8abf4-179">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台已經開啟，請重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8abf4-179">If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console is already opened, restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="8abf4-180">如果您使用 WCF-Custom 配接器，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，依序展開 [平台設定] 和 [主控件執行個體]，然後再重新啟動執行該配接器的 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8abf4-180">If you use the WCF-Custom adapter, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand Platform Settings, expand Host Instances, and then restart the BizTalk Host instance running the adapter.</span></span>  
  
3.  <span data-ttu-id="8abf4-181">如果您使用 WCF-CustomIsolated 配接器，請在 IIS 管理主控台中，重新啟動與 WCF 接收位置關聯的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="8abf4-181">If you use the WCF-CustomIsolated adapter, in the IIS Management console, restart the application pool associated with the WCF receive location.</span></span>  
  
4.  <span data-ttu-id="8abf4-182">如果您想要設定接收位置來使用 WCF 擴充性點，BizTalk 管理主控台中，展開  **BizTalk 群組**，依序展開 *\<BizTalk 應用程式 >*，依序展開**接收位置**，然後在右窗格中按兩下*\<接收位置>*。</span><span class="sxs-lookup"><span data-stu-id="8abf4-182">If you want to configure a receive location to use a WCF extensibility point, in the BizTalk Administration console, expand **BizTalk Group**, expand *\<BizTalk application>*, expand **Receive Locations**, and then in the right pane, double-click *\<Receive location>*.</span></span>  
  
    -   <span data-ttu-id="8abf4-183">在**接收位置屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**或**Wcf-customisolated**根據您想要使用，然後按一下 WCF 配接器**設定**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-183">In the **Receive Location Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom** or **WCF-CustomIsolated** depending on the WCF adapter that you want to use, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="8abf4-184">如果您想要設定傳送埠以使用 WCF 擴充性點，BizTalk 管理主控台中，展開  **BizTalk 群組**，依序展開 *\<BizTalk 應用程式 >*，依序展開  **傳送埠**，然後在右窗格中按兩下*\<傳送連接埠>*。</span><span class="sxs-lookup"><span data-stu-id="8abf4-184">If you want to configure a send port to use a WCF extensibility point, in the BizTalk Administration console, expand **BizTalk Group**, expand *\<BizTalk application>*, expand **Send Ports**, and then in the right pane, double-click *\<Send port>*.</span></span>  
  
    -   <span data-ttu-id="8abf4-185">在**傳送埠屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-185">In the **Send Port Properties** dialog box, in the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="8abf4-186">在 傳輸屬性對話方塊、 上**行為**索引標籤上，以滑鼠右鍵按一下**ServiceBehavior**或**endpointbehavior**依據行為延伸模組的類型然後，在**選取行為延伸模組**對話方塊中，選取行為延伸模組，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8abf4-186">In the transport properties dialog box, on the **Behavior** tab, right-click **ServiceBehavior** or **EndpointBehavior** depending on the type of the behavior extension, and then, in the **Select Behavior Extension** dialog box, select the behavior extension, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="8abf4-187">在傳輸屬性對話方塊中，設定其餘的傳輸設定。</span><span class="sxs-lookup"><span data-stu-id="8abf4-187">In the transport properties dialog box, configure the rest of the settings for the transport.</span></span>  
  
8.  <span data-ttu-id="8abf4-188">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，按一下關閉所有開啟的對話方塊**確定**按鈕，並確定沒有出現任何錯誤訊息和錯誤事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8abf4-188">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, close all open dialog boxes by clicking the **OK** buttons, and then make sure that no error messages and erroneous event logs appear.</span></span>  
  
### <a name="to-configure-a-wcf-custom-receive-location-with-an-ssl-certificate"></a><span data-ttu-id="8abf4-189">若要使用 SSL 憑證設定 WCF-Custom 接收位置</span><span class="sxs-lookup"><span data-stu-id="8abf4-189">To configure a WCF-Custom receive location with an SSL certificate</span></span>  
  
-   <span data-ttu-id="8abf4-190">如果 Wcf-custom 接收位置使用 HTTP 核心模式驅動程式 (HTTP.sys)，例如**httpsTransport**進行安全通訊端層 (SSL) 通訊，接收位置繫結項目，必須要有憑證針對每個通訊端 （IP 位址/連接埠組合） 登錄。</span><span class="sxs-lookup"><span data-stu-id="8abf4-190">If a WCF-Custom receive location happens to use the HTTP kernel-mode driver (HTTP.sys) such as the **httpsTransport** binding element, for Secure Sockets Layer (SSL) communications, the receive location must have a certificate registered for each socket (IP address/port combination).</span></span> <span data-ttu-id="8abf4-191">請使用 HttpCfg.exe 工具將 SSL 憑證繫結到電腦上的連接埠。</span><span class="sxs-lookup"><span data-stu-id="8abf4-191">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the computer.</span></span> <span data-ttu-id="8abf4-192">如需詳細資訊，請參閱 「 如何以:: 設定連接埠使用 SSL 憑證 」 在[http://go.microsoft.com/fwlink/?LinkId=86384](http://go.microsoft.com/fwlink/?LinkId=86384)。</span><span class="sxs-lookup"><span data-stu-id="8abf4-192">For more information, see "How To: Configure a Port with An SSL Certificate" at [http://go.microsoft.com/fwlink/?LinkId=86384](http://go.microsoft.com/fwlink/?LinkId=86384).</span></span>