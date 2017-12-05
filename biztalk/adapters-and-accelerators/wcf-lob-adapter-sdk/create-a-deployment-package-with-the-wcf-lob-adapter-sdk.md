---
title: "建立部署套件與 WCF LOB 配接器 SDK |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10022981-7944-45d6-a78a-4d680a79b010
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 734d79e92a4864090720434b9a1fb83387a0a850
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="create-a-deployment-package-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="f4796-102">使用 WCF LOB 配接器 SDK 建立部署套件</span><span class="sxs-lookup"><span data-stu-id="f4796-102">Create a deployment package with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="f4796-103">在開發週期中，您可以建置、 偵錯，並執行您在 Visual Studio 中的配接器。</span><span class="sxs-lookup"><span data-stu-id="f4796-103">During the development cycle, you can build, debug, and run your adapter within Visual Studio.</span></span> <span data-ttu-id="f4796-104">配接器解決方案的輸出是 DLL 的組件。</span><span class="sxs-lookup"><span data-stu-id="f4796-104">The output of an adapter solution is a DLL assembly.</span></span> <span data-ttu-id="f4796-105">您可以建置使用 Visual Studio IDE 介面卡方案，或使用 devenv.exe 指令碼建立配接器組件。</span><span class="sxs-lookup"><span data-stu-id="f4796-105">You can build your adapter solution using Visual Studio IDE or use the devenv.exe scripts to create an adapter assembly.</span></span> <span data-ttu-id="f4796-106">一旦開發配接器時，並且可供使用配接器取用者的環境中，您必須建立讓配接器安裝在測試環境和生產環境的部署封裝。</span><span class="sxs-lookup"><span data-stu-id="f4796-106">Once the adapter is developed and it is ready for use within the adapter consumer's environment, you must create a deployment package that allows the adapter to be installed in test and production environments.</span></span>  
  
 <span data-ttu-id="f4796-107">您可以加入方案中的 Visual Studio 安裝程式和部署專案。</span><span class="sxs-lookup"><span data-stu-id="f4796-107">You can include a Visual Studio Setup and Deployment project within the solution.</span></span> <span data-ttu-id="f4796-108">這可以用來自動產生的.msi 檔案做為方案組建的一部分。</span><span class="sxs-lookup"><span data-stu-id="f4796-108">This can be used to automatically generate an .msi file as part of the solution build.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4796-109">您可以防止安裝和部署專案建置您的本機工作站建置方案排除它透過 Configuration Manager （在 [建置] 功能表中） 在 Visual Studio.NET 中，以每一次。</span><span class="sxs-lookup"><span data-stu-id="f4796-109">You can prevent the Setup and Deployment project from building each time you build the solution on your local workstation by excluding it through the Configuration Manager (on the Build menu) within Visual Studio .NET.</span></span> <span data-ttu-id="f4796-110">如果您排除從使用此方法的方案建置的專案，您不會影響原始檔控制的方案檔。</span><span class="sxs-lookup"><span data-stu-id="f4796-110">If you exclude a project from a solution build using this method, you do not affect the source controlled solution file.</span></span> <span data-ttu-id="f4796-111">變更會被保留在方案使用者選項檔中，開發人員特定且不在原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="f4796-111">Changes are maintained within the solution user option file, which is developer-specific and not under source control.</span></span>  
  
 <span data-ttu-id="f4796-112">每當新的專案會加入至您的方案必須記得更新設定部署專案，以確保新的專案的輸出包含在.msi 檔案，而且會執行任何專案特定的安裝步驟。</span><span class="sxs-lookup"><span data-stu-id="f4796-112">Whenever new projects are added to your solution you must remember to update and configure the deployment project to ensure that the output of the new project is included within the .msi file and that any project-specific installation steps are performed.</span></span>  
  
 <span data-ttu-id="f4796-113">它不是足夠只在使用者電腦上安裝配接器專案的輸出。</span><span class="sxs-lookup"><span data-stu-id="f4796-113">It is not enough to just install the output of the adapter project on the user's computer.</span></span> <span data-ttu-id="f4796-114">配接器必須安裝在全域組件快取 (GAC)，並需要註冊配接器與更新 machine.config 檔案[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4796-114">The adapter needs to be installed in global assembly cache (GAC) and the machine.config file needs to be updated to register the adapter with [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="f4796-115">以下是可用來登錄或取消登錄與配接器的範例自訂動作[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4796-115">Following is a sample custom action that can be used to register or unregister an adapter with [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Configuration.Install;  
  
using System.Reflection;  
using System.ServiceModel.Configuration;  
using System.Diagnostics;  
using System.Configuration;  
  
namespace Microsoft.Adapters.Samples.EchoV2  
{  
    //Custom action to register the adapter with WCF configuration in machine.config   
  
    //<system.serviceModel>  
    //  <extensions>  
    //    <bindingElementExtensions>  
    //      <add name="{BINDINGELEM_NAME}" type="{BINDINGELEM_TYPE}, {Assembly Information}" />  
    //    </bindingElementExtensions>  
    //    <bindingExtensions>  
    //      <add name="{BINDING_NAME}" type="{BINDING_TYPE}, {Assembly Information}" />  
    //    </bindingExtensions>  
    //  </extensions>  
    //  <client>  
    //    <endpoint binding="{BINDING_NAME}" contract="IMetadataExchange" name="{BINDING_SCHEME}" />  
    //  </client>  
    //</system.serviceModel>  
  
    [RunInstaller(true)]  
    public partial class WCFLOBAdapterInstaller : Installer  
    {  
        private Assembly adapterAssembly;  
        private Type bindingSectionType;  
        private Type bindingElementExtensionType;  
        const string INSTALLER_PARM_INSTALLDIR = "INSTALLDIR";  
        const string BINDING_ASSEMBLY_NAME = "Microsoft.Adapters.Samples.EchoV2.EchoAdapter.dll";  
        const string BINDINGELEM_NAME = "echoAdapterV2";  
        const string BINDINGELEM_TYPE = "Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement";  
        const string BINDING_NAME = "echoAdapterBindingV2";  
        const string BINDING_TYPE = "Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement";  
        const string BINDING_SCHEME = "echov2";  
  
        /// <summary>  
        /// Constructor - initialize the components and register the event handlers  
        /// </summary>  
        public WCFLOBAdapterInstaller()  
        {  
            InitializeComponent();  
            this.AfterInstall += new InstallEventHandler(AfterInstallEventHandler);  
            this.BeforeUninstall += new InstallEventHandler(BeforeUninstallEventHandler);  
        }  
  
        /// <summary>  
        /// Add the WCF configuration information in machine.config when installing the adapter.  
        /// </summary>  
        /// <param name="sender"></param>  
        /// <param name="e"></param>  
        private void AfterInstallEventHandler(object sender, InstallEventArgs e)  
        {  
            try  
            {  
                Debug.Assert(this.Context != null, "Context of this installation is null.");  
                string path = this.Context.Parameters[INSTALLER_PARM_INSTALLDIR] + BINDING_ASSEMBLY_NAME;  
                adapterAssembly = Assembly.LoadFrom(path);  
                Debug.Assert(adapterAssembly != null, "Adapter assembly is null.");  
                bindingSectionType = adapterAssembly.GetType(BINDING_TYPE, true);  
                Debug.Assert(bindingSectionType != null, "Binding type is null.");  
                bindingElementExtensionType = adapterAssembly.GetType(BINDINGELEM_TYPE, true);  
                Debug.Assert(bindingElementExtensionType != null, "Binding element extension type is null.");  
                AddMachineConfigurationInfo();  
            }  
            catch (Exception ex)  
            {  
                throw new InstallException("Error while adding adapter configuration information. " + ex.InnerException.Message);  
            }  
        }  
  
        /// <summary>  
        /// Registers the adapter with the WCF configuration  
        /// NOTE: The   
        /// </summary>  
        public void AddMachineConfigurationInfo()  
        {  
            System.Configuration.Configuration config = ConfigurationManager.OpenMachineConfiguration();  
            Debug.Assert(config != null, "Machine.Config returned null");  
            // add <client><endpoint>               
            ServiceModelSectionGroup sectionGroup = config.GetSectionGroup("system.serviceModel") as ServiceModelSectionGroup;  
            if (sectionGroup != null)  
            {  
  
                bool channelEndpointElementExists = false;  
                // this call can throw an exception if there is problem   
                // loading endpoint configurations - e.g. each endpoint  
                // tries to load binding which in turn loads the DLL  
                ClientSection clientSection = sectionGroup.Client;  
                foreach (ChannelEndpointElement elem in clientSection.Endpoints)  
                {  
                    if (elem.Binding.Equals(BINDING_NAME, StringComparison.OrdinalIgnoreCase) && elem.Name.Equals(BINDING_SCHEME, StringComparison.OrdinalIgnoreCase) && elem.Contract.Equals("IMetadataExchange", StringComparison.OrdinalIgnoreCase))  
                    {  
                        channelEndpointElementExists = true;  
                        break;  
                    }  
                }  
                if (!channelEndpointElementExists)  
                {  
                    Debug.WriteLine("Adding ChannelEndpointElement for : " + BINDING_NAME);  
                    ChannelEndpointElement elem = new ChannelEndpointElement();  
                    elem.Binding = BINDING_NAME;  
                    elem.Name = BINDING_SCHEME;  
                    elem.Contract = "IMetadataExchange";  
                    sectionGroup.Client.Endpoints.Add(elem);  
                    Debug.WriteLine("Added ChannelEndpointElement for : " + BINDING_NAME);  
                }  
  
                // add <bindingElementExtension>  
                if (!sectionGroup.Extensions.BindingElementExtensions.ContainsKey(BINDINGELEM_NAME))  
                {  
                    ExtensionElement ext = new ExtensionElement(BINDINGELEM_NAME, bindingElementExtensionType.FullName + "," + bindingElementExtensionType.Assembly.FullName);  
                    sectionGroup.Extensions.BindingElementExtensions.Add(ext);  
                }  
  
                // add <bindingExtension>  
                if (!sectionGroup.Extensions.BindingExtensions.ContainsKey(BINDING_NAME))  
                {  
                    ExtensionElement ext = new ExtensionElement(BINDING_NAME, bindingSectionType.FullName + "," + bindingSectionType.Assembly.FullName);  
                    sectionGroup.Extensions.BindingExtensions.Add(ext);  
                }  
  
                config.Save();  
            }  
            else throw new InstallException("Machine.Config doesn't contain system.serviceModel node");  
        }  
  
        /// <summary>  
        /// Remove the machine configuration information when uninstalling the adapter  
        /// </summary>  
        /// <param name="sender"></param>  
        /// <param name="e"></param>  
        private void BeforeUninstallEventHandler(object sender, InstallEventArgs e)  
        {  
            try  
            {  
                RemoveMachineConfigurationInfo();  
            }  
            catch (Exception ex)  
            {  
                throw new InstallException("Error while removing adapter configuration information" + ex.InnerException.Message);  
            }  
        }  
  
        /// <summary>  
        /// Unregisters the adapter with WCF configuration  
        /// </summary>  
        public void RemoveMachineConfigurationInfo()  
        {  
            System.Configuration.Configuration config = ConfigurationManager.OpenMachineConfiguration();  
            Debug.Assert(config != null, "Machine.Config returned null");  
            ServiceModelSectionGroup sectionGroup = config.GetSectionGroup("system.serviceModel") as ServiceModelSectionGroup;  
            ChannelEndpointElement elemToRemove = null;  
            if (sectionGroup != null)  
            {  
                // Remove <client><endpoint>  
                foreach (ChannelEndpointElement elem in sectionGroup.Client.Endpoints)  
                {  
                    if (elem.Binding.Equals(BINDING_NAME, StringComparison.OrdinalIgnoreCase) && elem.Name.Equals(BINDING_SCHEME, StringComparison.OrdinalIgnoreCase) && elem.Contract.Equals("IMetadataExchange", StringComparison.OrdinalIgnoreCase))  
                    {  
                        elemToRemove = elem;  
                        break;  
                    }  
                }  
                if (elemToRemove != null)  
                {  
                    Debug.WriteLine("Removing ChannelEndpointElement for : " + BINDING_NAME);  
                    sectionGroup.Client.Endpoints.Remove(elemToRemove);  
                    Debug.WriteLine("Removed ChannelEndpointElement for : " + BINDING_NAME);  
                }  
                // Remove <bindingExtension> for this adapter  
                if (sectionGroup.Extensions.BindingExtensions.ContainsKey(BINDING_NAME))  
                {  
                    sectionGroup.Extensions.BindingExtensions.RemoveAt(BINDING_NAME);  
                }  
                // Remove <bindingElementExtension> for this adapter  
                if (sectionGroup.Extensions.BindingElementExtensions.ContainsKey(BINDINGELEM_NAME))  
                {  
                    sectionGroup.Extensions.BindingElementExtensions.RemoveAt(BINDINGELEM_NAME);  
                }  
                config.Save();  
            }  
            else  
            {  
                throw new InstallException("Machine.Config doesn't contain system.serviceModel node");  
            }  
        }  
  
        /// <summary>  
        /// Use this for testing outside of the Setup project  
        /// </summary>  
        /// <param name="assemblyDirectory">Directory where the adapter assembly is located</param>  
        public static void TestAddConfiguration(string assemblyDirectory)  
        {  
            WCFLOBAdapterInstaller action = new WCFLOBAdapterInstaller();  
            InstallContext context = new InstallContext();  
            // In the Setup project, this is set by selecting custom action  
            // and in Properties setting /INSTALLDIR="[TARGETDIR]\" for CustomActionData  
            context.Parameters.Add("INSTALLDIR", assemblyDirectory);  
            action.Context = context;  
            action.AfterInstallEventHandler(null, null);  
        }  
  
        /// <summary>  
        /// Use this for testing outside of the Setup project  
        /// </summary>  
        /// <param name="assemblyDirectory">Directory where the adapter assembly is located</param>  
        public static void TestRemoveConfiguration(string assemblyDirectory)  
        {  
            WCFLOBAdapterInstaller action = new WCFLOBAdapterInstaller();  
            InstallContext context = new InstallContext();  
            // In the Setup project, this is set by selecting custom action  
            // and in Properties setting /INSTALLDIR="[TARGETDIR]\" for CustomActionData  
            context.Parameters.Add("INSTALLDIR", assemblyDirectory);  
            action.Context = context;  
            action.BeforeUninstallEventHandler(null, null);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="f4796-116">如果您想要瀏覽範例配接器與部署套件，您可以下載完整的回應配接器，包括測試的程式碼和安裝指令碼。</span><span class="sxs-lookup"><span data-stu-id="f4796-116">If you want to explore a sample adapter with a deployment package, you can download a completed Echo Adapter including test code and installation script.</span></span> <span data-ttu-id="f4796-117">這個範例會在您 BizTalk 安裝檔案包含的`\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples`或`\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`。</span><span class="sxs-lookup"><span data-stu-id="f4796-117">This sample is included with your BizTalk installation files at `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` or `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f4796-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4796-118">See Also</span></span>  
 <span data-ttu-id="f4796-119">[部署配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md) </span><span class="sxs-lookup"><span data-stu-id="f4796-119">[Deploy an adapter using the WCF LOB adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md) </span></span>  
 [<span data-ttu-id="f4796-120">解除部署配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="f4796-120">Undeploy an adapter using the WCF LOB adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/undeploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)