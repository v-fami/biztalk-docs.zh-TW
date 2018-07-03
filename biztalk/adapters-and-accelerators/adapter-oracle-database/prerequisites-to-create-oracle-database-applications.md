---
title: 若要建立 Oracle 資料庫應用程式的必要條件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strong-name key file, creating a
ms.assetid: 7a6b2e50-8153-468c-a25e-c15612792773
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5ed7056ad860af9f54a247a7014189fb3b45527
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979975"
---
# <a name="prerequisites-to-create-oracle-database-applications"></a>若要建立 Oracle 資料庫應用程式的必要條件
您必須執行在開發 BizTalk 應用程式使用之前[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 區段也會列出一些用來開發 BizTalk 應用程式的 BizTalk Server 工具。  

## <a name="create-a-strong-named-key-file"></a>建立強式名稱金鑰檔

您必須建立強式名稱金鑰檔來建置專案，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 強式名稱包含專案的身分識別-其簡單文字名稱、 版本號碼和文化特性資訊 （如果有提供）;再加上公開金鑰和數位簽章。 強式名稱金鑰檔案包含公開金鑰和私密金鑰。  

> [!IMPORTANT]
>  建立強式名稱金鑰檔是一次性的工作。 您可以使用相同的金鑰，如您所開發的所有 BizTalk 應用程式。  

### <a name="prerequisites"></a>必要條件  
 您必須有 Microsoft[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]安裝在您要建立強式名稱金鑰的電腦上。  

### <a name="create-a-strong-name-key-file"></a>建立強式名稱金鑰檔  

1.  開啟 Visual Studio 開發人員命令提示字元。  

2.  在命令提示字元中，瀏覽至您要建立金鑰檔案的位置。 例如，輸入`cd C:\Sample`，然後按 ENTER 鍵。  

3.  在命令提示字元中輸入 `sn -k <key file name>.snk`，然後按下 ENTER。  

    > [!NOTE]
    >  您應該會收到訊息，指出金鑰組已寫入至強式名稱金鑰檔的命令提示字元。  

4.  在命令提示字元中輸入 `exit`，然後按下 ENTER。  

## <a name="learn-the-biztalk-server-tools"></a>了解 BizTalk Server 工具

如何使用主題[!INCLUDE[adapteroracle_short_md](../../includes/adapteroracle-short-md.md)]中[開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)都已寫明是假設您有數個實用知識，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]工具。 您可以使用下列工具來開發 BizTalk 應用程式使用[!INCLUDE[adapteroracle_md](../../includes/adapteroracle-md.md)]:  

- Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] 

- BizTalk Explorer (BizTalk 總管)  

- 協調流程 eesigner  

- 管線設計師  

- BizTalk 對應工具  

- BizTalk Server 管理主控台  

### <a name="prerequisites"></a>必要條件  
 您必須先安裝 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]才能存取[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]工具。  

### <a name="biztalk-server-tools"></a>BizTalk Server 工具  
 下表包含主題[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]文件說明如何使用每個列出的工具。  


|                                   工具                                    |                                                                                                                                                                                              中的主題[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]核心文件集                                                                                                                                                                                               |
|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] | -   [使用 Visual Studio](../../core/using-visual-studio.md) <br />-   [使用 BizTalk 專案](../../core/working-with-biztalk-projects.md)<br />-   [部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)<br /><br /> 深入了解 Visual Studio 方案、 專案和項目會在[Visual Studio 中方案和專案](https://msdn.microsoft.com/library/b142f8e7.aspx)。 |
|                          協調流程設計師                           |                                                                                                                                                                                          [使用協調流程設計師建立協調流程](../../core/creating-orchestrations-using-orchestration-designer.md)                                                                                                                                                                                           |
|                             管線設計師                             |                                                                                                                                                                                                    [使用管線設計師建立管線](../../core/creating-pipelines-using-pipeline-designer.md)                                                                                                                                                                                                     |
|                              BizTalk Mapper (BizTalk 對應工具)                               |                                                                                                                                                                                                            [使用 BizTalk 對應工具建立對應](../../core/creating-maps-using-biztalk-mapper.md)                                                                                                                                                                                                             |
|                   BizTalk Server 管理主控台                   |                                                                                                                                                                                               [使用 BizTalk Server 管理主控台](../../core/using-the-biztalk-server-administration-console.md)                                                                                                                                                                                                |

## <a name="next"></a>下一個
[若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)