---
title: "設定環境的語彙基元和自動部署的變數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 28bb2d4a-f45c-466d-ba65-0ca8cad0bffd
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 7d148f79fceb68b24feb45882ab89767369ed7e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-environmental-tokens-and-variables-for-automatic-deployment"></a>設定環境的語彙基元和自動部署的變數
使用 Visual Studio Team Services (VSTS) 變數，在您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]繫結檔案。

## <a name="overview"></a>概觀
在 VSTS 環境中，您可以加入變數，並設為值。 例如，您可以建立*sendPortPath*變數，並將其值設定在實體資料夾您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 

內[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]應用程式繫結檔案，可設定的變數可以是任何項目內的 XML 標記，例如接收位置名稱、 主機、 傳送埠的 URI，等等。 

這些變數專屬於您 VSTS 的環境，而且可用來部署至多個相同的應用程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。 

在本主題中，我們會示範如何新增 VSTS 中的變數繫結檔案，以及如何建立在 VSTS 中的變數。 

## <a name="configure-the-variables-in-your-biztalk-binding-file"></a>BizTalk 繫結檔案中設定的變數

下列範例是屬於[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]繫結檔案，並示範如何套用語彙基元。

1. 開啟應用程式繫結檔案：

    ![BizTalk Feature Pack 1 繫結 1](../core/media/biztalk-feature-pack-1-binding-1.png)

2. 尋找您想要變更的項目：

    ![BizTalk Feature Pack 2 的繫結的 1](../core/media/biztalk-feature-pack-1-binding-2.png)
    
3. 移除填入的值，以取代您變數： `$(YourValue)`。 例如，輸入`$(SendPort1)`: 

    ![BizTalk Feature Pack 1 繫結 3](../core/media/biztalk-feature-pack-1-binding-3.png)


4. 完成時，儲存繫結檔案，並將它套用到您的 JSON 建置範本。
5. 登入至 Visual Studio Team 服務方案，並選取**組建與版本**。
6. 移至**發行**。 選取您**發行定義**，或建立新的連線。
7. 在下**環境**，選取**加入新的環境**，或變更現有的環境： 

    ![加入新的環境](../core/media/add-a-new-environment.png)

8. 按一下省略符號，然後選取**設定變數**:

    ![設定變數](../core/media/configure-variables.png)

9. 藉由新增每個環境中，使用繫結檔中建立的語彙基元名稱的變數中，您可以部署至具有不同值的多個環境的應用程式：

    ![環境特定變數](../core/media/environment-specific-variables.png)
    
10. 選取**確定**儲存新變數。
11. 一旦起始組建時，這些值會加入從繫結檔案。

## <a name="next-step"></a>下一步
[加入 VSTS BizTalk 應用程式](../core/add-a-biztalk-server-application-to-visual-studio-team-services.md)