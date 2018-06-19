---
title: 啟用 WCF 擴充性點，WCF 配接器 |Microsoft 文件
description: 安裝組件、 設定 machine.config，將副檔名新增至 BizTalk 管理、 建立接收位置，才能啟用 WCF 配接器在 BizTalk Server 中的 WCF 擴充性點
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c2af105-5272-4a6a-95d2-066312ab788e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2881ddd83ebeb31a9f5ff3da6ed858f158751d64
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975412"
---
# <a name="how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters"></a>如何使用 WCF 配接器啟用 WCF 擴充性點
啟用三個 WCF 擴充性點： 行為延伸模組、 繫結元素延伸模組，以及繫結延伸模組，使用 Wcf-custom 和 Wcf-customisolated 配接器。 為了執行這項操作，您會先將實作 WCF 擴充性點的組件安裝在全域組件快取 (GAC) 中，接著修改電腦上的 machine.config 檔案，然後再使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台設定 WCF-Custom 或 WCF-CustomIsolated 配接器。  
  
請參閱[延伸 WCF](https://docs.microsoft.com/dotnet/framework/wcf/extending/extending-wcf)如需 WCF 擴充性點的詳細資訊。
  
 
## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。 [部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)提供詳細的資訊。  
  
## <a name="install-assemblies-implementing-a-wcf-extensibility-point-in-the-gac"></a>安裝在 GAC 中實作 WCF 擴充性點的組件  
  
1.  將實作 WCF 擴充性點的組件複製到本機電腦的資料夾。  
  
2.  將 WCF 擴充性點使用的組件 (如果有的話) 複製到本機電腦的資料夾。  
  
3.  啟動**Visual Studio 命令提示字元**。  
  
4.  輸入以下命令：  
  
     **gacutil.exe /if"\<**  *組件.dll 檔案路徑*  **\>"**  
  
5.  這會將組件安裝至 GAC，覆寫任何同名的現有組件。  
  
6.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令提示字元下，針對您在本程序步驟 1 和 2 中複製的所有組件重複步驟 4 和 5。  
  
7.  如果您有多個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦和管理電腦，重複步驟 1 到 6，此程序的所有電腦上。  
  
    > [!NOTE]
    >  若要啟用 WCF 配接器的 WCF 擴充性點，執行配接器的 BizTalk 主控件執行個體必須能夠在執行階段載入實作 WCF 擴充性點的組件。  
  
## <a name="configure-the-machineconfig-file-for-a-wcf-binding-extension"></a>設定 WCF 繫結延伸模組的 machine.config 檔案  
  
1.  在命令提示字元中，移至 %frameworkdir%\v4。X.XXXXX\CONFIG 資料夾，然後開啟**machine.config**使用 [記事本] 檔案。  
  
2.  在記事本中，如果 machine.config 檔案沒有 **\<system.serverModel\>\\< 延伸\>** 項目，加入這些項目內 **\<組態\>** 元素的 machine.config 檔案，然後再加入 **\<bindingExtensions\>**  WCF 繫結延伸模組內的項目 **\<system.serverModel\>\\< 延伸\>** 項目。 例如，若要啟用自訂繫結延伸模組 netHttpBinding，請加入內的下列程式碼**\<組態\>** machine.config 檔案的項目：  
  
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
    >  - 您可以找到要使用命令，註冊的組件的資訊**gacutil /lr** *< assembly_name>*。  
    >  - 請參閱[bindingExtensions](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/wcf/bindingextensions)這個項目上。
  
3.  在「記事本」中，儲存 machine.config 檔案。  
  
4.  如果您有多部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦和管理電腦，請在所有電腦上重複本程序的步驟 1 到 3。  
  
    > [!NOTE]
    >  您必須在所有電腦上重複這些步驟，WCF 基礎結構才能處理 BizTalk 主控件執行個體和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台的 WCF 擴充性點。  
  
## <a name="configure-a-wcf-binding-extension-by-using-the-biztalk-administration-console"></a>使用 BizTalk 管理主控台設定 WCF 繫結延伸模組  
  
1.  開啟 [BizTalk Server 管理] 。  
  
    > [!NOTE]
    >  如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台已經開啟，請重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。  
  
2.  如果您使用 WCF-Custom 配接器，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，依序展開 [平台設定] 和 [主控件執行個體]，然後再重新啟動執行該配接器的 BizTalk 主控件執行個體。  
  
3.  如果您使用 WCF-CustomIsolated 配接器，請在 IIS 管理主控台中，重新啟動與 WCF 接收位置關聯的應用程式集區。  
  
4.  如果您想要設定接收位置中使用 WCF 擴充性點，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk 群組**，依序展開 *\<BizTalk 應用程式\>*，依序展開**接收位置**，然後在右窗格中按兩下*\<接收位置\>*。  
  
    -   在**接收位置屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**或**Wcf-customisolated**根據您想要使用，然後按一下 WCF 配接器**設定**。  
  
5.  如果您想要設定傳送埠中使用 WCF 擴充性點，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk 群組**，依序展開 *\<BizTalk 應用程式\>*，依序展開**傳送埠**，然後在右窗格中按兩下*\<傳送埠\>*。  
  
    -   在**傳送埠屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
6.  在 傳輸屬性對話方塊、 上**繫結**索引標籤上選取繫結延伸模組，然後設定其餘的傳輸設定。  
  
7.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，按一下關閉所有開啟的對話方塊**確定**按鈕，並確定沒有出現任何錯誤訊息和錯誤事件記錄檔。  
  
## <a name="configure-the-machineconfig-file-for-a-wcf-binding-element-extension"></a>設定 WCF 繫結元素延伸模組的 machine.config 檔案  
  
1.  在命令提示字元中，移至 %frameworkdir%\v4。X.XXXXX\CONFIG 資料夾，然後開啟**machine.config**使用 [記事本] 檔案。  
  
2.  在記事本中，如果 machine.config 檔案沒有 **\<system.serverModel\>\\< 延伸\>** 項目，加入這些項目內 **\<組態\>** 元素的 machine.config 檔案，然後再加入 **\<bindingElementExtensions\>**  WCF 繫結項目的項目延伸模組內 **\<system.serverModel\>\\< 延伸\>** 項目。 比方說，若要啟用自訂繫結元素延伸模組，請將下列程式碼內**\<組態\>** machine.config 檔案的項目：  
  
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
    > - 您可以找到要使用命令，註冊的組件的資訊**gacutil /lr** *< assembly_name>*。  
    > - 請參閱[bindingElementExtensions](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/wcf/bindingelementextensions)這個項目上。
  
3.  在「記事本」中，儲存 machine.config 檔案。  
  
4.  如果您有多部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦和管理電腦，請在所有電腦上重複本程序的步驟 1 到 3。  
  
    > [!NOTE]
    >  您必須在所有電腦上重複這些步驟，WCF 基礎結構才能處理 BizTalk 主控件執行個體和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台的 WCF 擴充性點。  
  
## <a name="configure-a-wcf-binding-element-extension-by-using-the-biztalk-administration-console"></a>使用 BizTalk 管理主控台設定 WCF 繫結元素延伸模組  
  
1.  開啟 [BizTalk Server 管理] 。  
  
    > [!NOTE]
    >  如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台已經開啟，請重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。  
  
2.  如果您使用 WCF-Custom 配接器，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，依序展開 [平台設定] 和 [主控件執行個體]，然後再重新啟動執行該配接器的 BizTalk 主控件執行個體。  
  
3.  如果您使用 WCF-CustomIsolated 配接器，請在 IIS 管理主控台中，重新啟動與 WCF 接收位置關聯的應用程式集區。  
  
4.  如果您想要設定接收位置中使用 WCF 擴充性點，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk 群組**，依序展開 *\<BizTalk 應用程式\>*，依序展開**接收位置**，然後在右窗格中按兩下*\<接收位置\>*。  
  
    -   在**接收位置屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**或**Wcf-customisolated**根據您想要使用，然後按一下 WCF 配接器**設定**。  
  
5.  如果您想要設定傳送埠中使用 WCF 擴充性點，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk 群組**，依序展開 *\<BizTalk 應用程式\>*，依序展開**傳送埠**，然後在右窗格中按兩下*\<傳送埠\>*。  
  
    -   在**傳送埠屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
6.  在 傳輸屬性對話方塊、 上**繫結**索引標籤的**繫結的型別**下拉式清單中，選取**customBinding**。  
  
7.  在 傳輸屬性對話方塊、 上**繫結**索引標籤上，以滑鼠右鍵按一下工作區**繫結**清單，然後再按**將延伸加入**。  
  
8.  在**選取繫結元素延伸模組**對話方塊中，選取繫結項目延伸，，然後按一下**確定**。  
  
9. 在 傳輸屬性對話方塊、 上**繫結**索引標籤上，調整繫結項目中加入的順序**繫結**清單取決於您在加入的繫結項目延伸的類型如下所示的上一個步驟：  
  
    -   在**繫結**清單中，繫結項目延伸，以滑鼠右鍵按一下，然後按一下 **移延伸模組**或**下移延伸模組**。 最低的繫結項目延伸中**繫結**對應至通道堆疊的底部元件的清單。 中最高的繫結項目**繫結**清單對應於通訊堆疊的最上層元件。  
  
        > [!NOTE]
        >  請參閱[自訂繫結](https://docs.microsoft.com/dotnet/framework/wcf/extending/custom-bindings)自訂繫結的特定繫結項目順序的詳細資料。
  
10. 在傳輸屬性對話方塊中，設定其餘的傳輸設定。  
  
11. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，按一下關閉所有開啟的對話方塊**確定**按鈕，並確定沒有出現任何錯誤訊息和錯誤事件記錄檔。  
  
## <a name="configure-the-machineconfig-file-for-a-wcf-behavior-extension"></a>設定 WCF 行為延伸模組的 machine.config 檔案  
  
1.  在命令提示字元中，移至 %frameworkdir%\v4。X.XXXXX\CONFIG 資料夾，然後開啟**machine.config**使用 [記事本] 檔案。  
  
2.  在記事本中，如果 machine.config 檔案沒有 **\<system.serverModel\>\\< 延伸\>** 項目，加入這些項目內 **\<組態\>** 元素的 machine.config 檔案，然後再加入 **\<behaviorExtensions\>**  WCF 行為延伸模組項目內部 **\<system.serverModel\>\\< 延伸\>** 項目。 比方說，若要啟用自訂行為延伸模組 schemaValidator，請將下列程式碼內**\<組態\>** machine.config 檔案的項目：  
  
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
    >  - 您可以找到要使用命令，註冊的組件的資訊**gacutil /lr** *< assembly_name>*。  
    >  - 請參閱[behaviorExtensions](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/wcf/behaviorextensions)這個項目上。
  
3.  在「記事本」中，儲存 machine.config 檔案。  
  
4.  如果您有多部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦和管理電腦，請在所有電腦上重複本程序的步驟 1 到 3。  
  
    > [!NOTE]
    >  您必須在所有電腦上重複這些步驟，WCF 基礎結構才能處理 BizTalk 主控件執行個體和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台的 WCF 擴充性點。  
  
## <a name="configure-a-wcf-behavior-extension-by-using-the-biztalk-administration-console"></a>使用 BizTalk 管理主控台設定 WCF 行為延伸模組  
  
1.  開啟 [BizTalk Server 管理] 。  
  
    > [!NOTE]
    >  如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台已經開啟，請重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。  
  
2.  如果您使用 WCF-Custom 配接器，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，依序展開 [平台設定] 和 [主控件執行個體]，然後再重新啟動執行該配接器的 BizTalk 主控件執行個體。  
  
3.  如果您使用 WCF-CustomIsolated 配接器，請在 IIS 管理主控台中，重新啟動與 WCF 接收位置關聯的應用程式集區。  
  
4.  如果您想要設定接收位置來使用 WCF 擴充性點，BizTalk 管理主控台中，展開  **BizTalk 群組**，依序展開 *\<BizTalk 應用程式\>*，依序展開**接收位置**，然後在右窗格中按兩下*\<接收位置\>*。  
  
    -   在**接收位置屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**或**Wcf-customisolated**根據您想要使用，然後按一下 WCF 配接器**設定**。  
  
5.  如果您想要設定傳送埠以使用 WCF 擴充性點，BizTalk 管理主控台中，展開  **BizTalk 群組**，依序展開 *\<BizTalk 應用程式\>*，展開**傳送埠**，然後在右窗格中按兩下*\<傳送埠\>*。  
  
    -   在**傳送埠屬性**對話方塊中，於**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
6.  在 傳輸屬性對話方塊、 上**行為**索引標籤上，以滑鼠右鍵按一下**ServiceBehavior**或**endpointbehavior**依據行為延伸模組的類型然後，在**選取行為延伸模組**對話方塊中，選取行為延伸模組，然後按一下**確定**。  
  
7.  在傳輸屬性對話方塊中，設定其餘的傳輸設定。  
  
8.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，按一下關閉所有開啟的對話方塊**確定**按鈕，並確定沒有出現任何錯誤訊息和錯誤事件記錄檔。  
  
## <a name="configure-a-wcf-custom-receive-location-with-an-ssl-certificate"></a>設定 WCF 自訂接收位置使用 SSL 憑證  
  
-   如果 Wcf-custom 接收位置使用 HTTP 核心模式驅動程式 (HTTP.sys)，例如**httpsTransport**進行安全通訊端層 (SSL) 通訊，接收位置繫結項目，必須要有憑證針對每個通訊端 （IP 位址/連接埠組合） 登錄。 請使用 HttpCfg.exe 工具將 SSL 憑證繫結到電腦上的連接埠。 如需詳細資訊，請參閱[How To： 使用 SSL 憑證設定連接埠](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate)。