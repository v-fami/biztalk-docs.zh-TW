---
redirect_url: /biztalk/core/feature-pack-add-build-release-definitions/
redirect_document_id: true
ROBOTS: NOINDEX
title: 設定要部署 BizTalk Server 方案或專案的 Visual Studio Team Services |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2555712a-dfe4-420e-9a61-1d1a6d98c322
caps.latest.revision: 6
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 8b13ef6f56e892bb3598096272d876c5f0a865f3
ms.sourcegitcommit: be6273d612669adfbb9dc9208aaae0a8437d4017
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2018
ms.locfileid: "52826302"
---
# <a name="configure-visual-studio-team-services-to-deploy-biztalk-server-solutions-or-projects"></a>設定要部署 BizTalk Server 方案或專案的 Visual Studio Team Services
設定 VSTS 自動部署[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]專案。 

**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，您可以自動建置您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]使用 Visual Studio Team Services (VSTS) 的解決方案。 

本主題說明如何安裝和設定 Visual Studio Team Service (VSTS) BizTalk 使用自動部署。 

> [!IMPORTANT]
> VSTS 代理程式只能安裝在上一個[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]群組中。 

## <a name="prerequisites"></a>先決條件

* 安裝[Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100)上您 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* 一些經驗及建立與使用定義在 VSTS 中的知識。 如果您是新手 VSTS，這些可能是不錯的資源： 

  [Visual Studio Team Services 概觀](https://www.visualstudio.com/docs/overview)  
  [新手的 CI/CD](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)
  

## <a name="create-a-vsts-account-and-create-a-definition"></a>建立 VSTS 帳戶，並建立定義

1. 在 web 瀏覽器中，移至您[Visual Studio online 設定檔](https://app.vsaex.visualstudio.com/go/profile)、 登入，然後選取**建立新帳戶**:

    ![建立新帳戶](../core/media/create-a-new-account.png)

2. 輸入帳戶的名稱，選取您偏好的原始檔的程式碼存放庫，然後選取**繼續**:

    ![建立新的專案](../core/media/create-a-new-project.png)

3. 建立新的帳戶時，與類似於站台`https://YourAccountName.visualstudio.com/MyFirstProject`隨即開啟。
    
4. 安裝[部署 BizTalk 應用程式服務](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application)至您剛才建立的帳戶。

    ![建立新的版本](../core/media/build-new-release.png)

5. 您可能會收到一些提示。 確認以繼續。 請確定您已登入您的專案，在 VSTS 中。

6. 選取 **組建和發行**，然後建立**新增**組建定義：

    ![選取的組建和發行](../core/media/select-build-and-release.png)

    > [!TIP]
    > 確定您是在`https://YourAccountName.visualstudio.com/MyFirstProject`。 否則**新增**或是**新的定義**按鈕可能不會有。 
    
7. 選取 [ **Visual Studio**範本，然後選取**下一步]**:

    ![選取 visual studio，然後按一下 下一步](../core/media/select-visual-studio-and-click-next.png)

8. 檢閱您的設定，然後選取**建立**。

9. 刪除您不需要的步驟。 本教學課程中，您可以刪除下列項目： 
10. NuGet 還原
11. 測試組件
12. 發行符號路徑 

      ![刪除不需要的步驟](../core/media/delete-steps-not-needed.png)

13. **選擇性**。 如果您想要啟用持續整合 (CI) 中，選取**觸發程序**功能表中，核取**連續整合 (CI)**。

接下來，將代理程式安裝在您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 

## <a name="install-the-agent"></a>安裝代理程式

運作的解決方案，讓本機電腦上的私人 Windows 代理程式。 請記住，**必須只有其中安裝代理程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]群組中**。 

1. 在定義中，選取**一般**（頂端） 索引標籤。
2. 針對**預設代理程式佇列**屬性中，選取**預設**從清單中的代理程式。 
3. 選取 **管理**旁**預設代理程式佇列**屬性。 新的瀏覽器索引標籤隨即開啟。

    ![建立新的管理代理程式](../core/media/create-new-management-agent.png)

4. 在左窗格中，會選取預設佇列。 如果代理程式已列出，且在線上，您已大功告成。 您有代理程式，安裝並執行。 

    如果未列出的代理程式，然後選取**下載代理程式**，並繼續進行安裝程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 **移至[代理程式部署到 Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows)的完整步驟**安裝代理程式，並啟動代理程式。 

    > [!IMPORTANT]
    > 請遵循所有的步驟[代理程式部署到 Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows)。 請勿略過此步驟。 

5. 預設代理程式**線上**返回**一般**索引標籤上，在定義中，並確認**預設**選取**預設代理程式佇列**.
6. **儲存**並**新組建排入佇列**。

接下來，建立 BizTalk Server 應用程式部署定義。

## <a name="create-the-biztalk-deployment-definition"></a>建立 BizTalk 部署定義

1. 選取 **組建**索引標籤上，選取**所有定義**，然後選取**新增**:

    ![建立新的發行定義](../core/media/create-new-release-definition.png)

2. 選取 [**空**範本，然後選取**下一步]**:

    ![從空白範本建立新的定義](../core/media/create-new-definition-from-an-empty-template.png)

3. 選取您**儲存機制**來源並**分支**定義。
4. **選擇性**。 選取 **持續整合**。
5. 選取 **預設**代理程式從該佇列清單，然後選取**建立**。
6. **新增組建步驟**，選取**BizTalk Server 應用程式部署**工作，並選取**新增**。 **關閉**工作目錄中。

    ![加入新的部署定義](../core/media/add-new-deploy-definition.png)

7. 選取 **作業名稱**您想要使用：

    * **建立新的 BizTalk 應用程式**部署新的應用程式。 如果應用程式已經存在，它會解除安裝目前的應用程式 （句點），並安裝新的應用程式。 如果已啟用持續整合，它會自動重新部署應用程式更新存放庫中時。
    * **更新現有的 BizTalk 應用程式**附加的變更，例如**結構描述**已在執行的應用程式。 它不需要完整的重新部署應用程式。

8. 請輸入**應用程式名稱**中您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。
9. 在 **部署套件路徑**，選取您的存放庫中的 zip 檔案的路徑。
10. 選取 **觸發程序**從功能表中，啟用**連續整合**，然後選取正確**分支**組建。
11. 選取 **儲存**:

    ![儲存新的組建定義](../core/media/save-the-new-build-definition.png)

12. 指定新**定義**，而且設定正確的路徑。 
13. 定義儲存之後，選取**新的組建排入佇列**。 然後，選取**佇列代理程式**，並將註解新增至認可。
