---
redirect_url: /biztalk/core/mqseries-adapter-deployment-options
redirect_document_id: 
ROBOTS: NOINDEX
ms.openlocfilehash: 2aa74be2d86bcb8f32661fdcf06727eb6391861d
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="using-mqseries-adapter-with-an-earlier-version-of-the-adapter"></a>以舊版配接器使用 MQSeries 配接器
MQSeries 配接器的不同 BizTalk Server 版本可以全部使用相同的遠端 WebSphere MQ Server 上的 Windows。 MQSeries 어댑터에 사용되는 다음 버전의 COM+ 응용 프로그램을 같은 WebSphere MQSeries 컴퓨터에서 함께 사용할 수 있기 때문입니다.  
  
-   **MQSAgent (MQSAgent2) COM + 應用程式**MQSeries 配接器 (BizTalk Server 2006) 搭配使用 
  
-   **MQSAgent COM + 應用程式**MQSeries 配接器 (BizTalk Server 2004) 搭配使用  
  
-   **MQHelper COM + 應用程式**MQSeries 配接器 (BizTalk Server 2002) 搭配使用 
  
> [!NOTE]
>  이러한 COM+ 응용 프로그램을 함께 설치하도록 구성하는 경우 해당 응용 프로그램 중 같은 MQSeries 큐를 사용하도록 구성되지 않은 응용 프로그램이 있는지 확인해야 합니다.  
  
> [!IMPORTANT]
>  如果未安裝舊版的 BizTalk Server 上的 WebSphere MQSeries Adapter COM + 應用程式版本與舊版 MQSeries Adapter COM + 應用程式的 BizTalk Server 2006-並存安裝才支援MQSeries 電腦中。  
  
### <a name="to-install-the-biztalk-server-2006-version-of-the-mqseries-adapter-com-application-on-a-websphere-mqseries-computer-that-is-running-an-earlier-version-of-the-mqseries-adapter-com-application"></a>이전 버전의 MQSeries 어댑터 COM+ 응용 프로그램을 실행 중인 WebSphere MQSeries 컴퓨터에 BizTalk Server 2006 버전의 MQSeries 어댑터 COM+ 응용 프로그램을 설치하려면  
  
1.  從 BizTalk Server 2006 CD，若要將相依檔案 MSVCR80.dll 和 MSVCP80.dll 複製到 WebSphere MQSeries 電腦的 \Platform\BootStrap\ 目錄執行 Bootstrap.msi。  
  
2.  將 MQSAgent.dll 檔案從 BizTalk Server 2006 CD 的 \Msi\Program Files\ 目錄複製到 WebSphere MQSeries 電腦中。  
  
    > [!NOTE]
    >  또한 MQSAgent 추적 유틸리티를 사용하려는 경우 이 디렉터리에서 WebSphere MQSeries 컴퓨터로 MQSTrace.cmd 파일을 복사합니다. 如需 MQSAgent 追蹤公用程式請參閱[使用追蹤工具分析 MQSeries 配接器錯誤](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md)。  
  
3.  WebSphere MQSeries 컴퓨터에서 regsvr32 mqsagent.dll을 실행하여 MQSAgent.dll에 구성 요소를 수동으로 등록합니다.  
  
    ```  
    regsvr32 MQSAgent.dll  
    ```  
  
    > [!NOTE]
    >  MQSAgent.dll을 복사한 대상 디렉터리에서 이 명령을 실행합니다.  
  
4.  MQSAgent 구성 요소에 대한 새 COM+ 응용 프로그램을 만듭니다.  
  
    -   以滑鼠右鍵按一下 COM + 應用程式中，按一下 **新增**, ，**應用程式** 顯示 **COM + 應用程式安裝精靈** 按一下 **下一步**。  
  
    -   按一下  **建立空的應用程式**。  
  
    -   輸入名稱 **MQSAgent2**, ，保留預設選項為 **伺服器應用程式** 啟用，而且按一下 **下一步**。  
  
    -   選取的選項 **這位使用者**, 、 輸入適當的帳戶資訊，然後按一下  **下一步**。  
  
        > [!NOTE]
        >  이 계정에는 해당 IBM WebSphere MQ 큐에 대한 연결 권한과 넣기 및/또는 가져오기 권한이 있어야 합니다.  
  
    -   按一下  **下一步** 在 新增 **應用程式角色** 對話方塊。  
  
    -   按一下  **下一步** 上 **將使用者新增至角色** 對話方塊。  
  
    -   **마침**을 클릭합니다.  
  
5.  MQSAgent2 COM+ 응용 프로그램에 MQSAgent.dll 구성 요소를 추가합니다.  
  
    -   按一下以展開 **MQSAgent2** COM + 應用程式。  
  
    -   以滑鼠右鍵按一下 **元件** 按一下 **新增**, ，**元件** 以啟動 [COM + 元件安裝精靈]，然後按一下 **下一步**。  
  
    -   按一下  **安裝新元件**, ，瀏覽至 MQSAgent.dll 檔案，然後按一下 **開啟**。  
  
    -   **다음**을 클릭한 다음 **마침**을 클릭합니다.  
  
## <a name="see-also"></a>另請參閱  
 [使用 MQSeries 配接器](../core/using-the-mqseries-adapter.md)