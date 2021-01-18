# javawebapp
package lesson03.servlets;

import java.io.IOException;

import javax.servlet.Servlet;
import javax.servlet.ServletConfig;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;

public class HelloWorld implements Servlet {
	ServletConfig config;

	/*
	 init()
	  서블릿 컨테이너가 서블릿을 생성한 후 초기화 작업을 수행하기 위해 호출하는 메서드 
	  서블릿이 클라이언트의 요청을 처리하기 전에 준비할 작업이 있다면 이 메서드에 작성
	  예 : 이 메서드가 호출될 때 DB에 연결하거나 외부 스토리지 서버와의 연결, 프로퍼티 로딩 등 
	  클라이언트 요청을 처리하는데 필요한 자원을 미리 준비할 수 있음
	 */
	@Override
	public void init(ServletConfig config) throws ServletException {
		System.out.println("init() 호출됨");
		this.config = config;
	}

	/* 
	 service()
	 클라이언트가 요청할 때 마다 호출되는 메서드
	 실질적으로 서비스 작업을 수행하는 메서드
	 이 메서드에 서블릿이 해야 할 일을 작성
	 */
	@Override
	public void service(ServletRequest req, ServletResponse res) throws ServletException, IOException {
		System.out.println("service() 호출됨");
	}
	
	/*
	 destroy()
	 서블릿 컨테이너가 종료되거나 웹 애플리케이션이 멈출 때,
	 또는 해당 서블릿을 비활성화 시킬 때 호출됨
	 이 메서드에는 서비스 수행을 위해 확보했던 자원을 해제한다거나 데이터를 저장하는 등
	 마무리 작업을 작성하면 됨
	 */
	@Override
	public void destroy() {
		System.out.println("destroy() 호출됨");
	}

	@Override
	public ServletConfig getServletConfig() {
		System.out.println("getServletConfig() 호출됨");
		return this.config;
	}

	@Override
	public String getServletInfo() {
		System.out.println("getServletInfo() 호출됨");
		return "version=1.0;author=eomjinyoung;copyright=eomjinyoung 2013";
	}


}
