---
title: 若要建立的 SAP 應用程式的必要條件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51ae9569-4081-4142-9ee2-8ae0069e9d90
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72225a059d5b655555f46f06758df11de3eaa8e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978567"
---
# <a name="prerequisites-to-create-sap-applications"></a>若要建立的 SAP 應用程式的必要條件
本節提供有關開發 BizTalk 應用程式使用之前，您必須執行的工作資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 區段也會列出一些用來開發 BizTalk 應用程式的 BizTalk Server 工具。  

## <a name="create-a-strong-name-key-file"></a>建立強式名稱金鑰檔

您必須建立強式名稱金鑰檔來建置專案，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 強式名稱包含專案的身分識別-其簡單文字名稱、 版本號碼和文化特性資訊 （如果有提供）-加上公開金鑰和數位簽章。 強式名稱金鑰檔案包含公開金鑰和私密金鑰。  

> [!IMPORTANT]
>  建立強式名稱金鑰檔是一次性的工作。 您可以使用相同的金鑰，如您所開發的所有 BizTalk 應用程式。  

1.  開啟 Visual Studio 開發人員命令提示字元。  

2.  在命令提示字元中瀏覽至您要建立金鑰檔案的位置。 例如，輸入**cd C:\Sample**，然後按 ENTER 鍵。  

3.  在命令提示字元中輸入 `sn -k <key file name\>.snk`，然後按下 ENTER。  

    > [!NOTE]
    >  您應該會收到訊息，指出金鑰組已寫入至強式名稱金鑰檔的命令提示字元。  

4.  在命令提示字元中，輸入**結束**，然後按 ENTER 鍵。  

## <a name="learn-the-biztalk-server-tools"></a>了解 BizTalk Server 工具

如何使用主題[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]中[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)假設您有數個 BizTalk Server 工具的實用知識。 您將使用下列工具來開發 BizTalk 應用程式使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  

- Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] 

- 協調流程 eesigner  

- 管線設計師  

- BizTalk 對應工具  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 管理主控台  


### <a name="prerequisites"></a>必要條件  
 您必須安裝 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 才能存取 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 工具。  

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
[建立 SAP 應用程式的建構元素](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)